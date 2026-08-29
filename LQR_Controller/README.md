# Active Suspension Control of a 2-DOF Quarter-Car Model

MATLAB/Simulink implementation of passive suspension optimization and LQR-based active suspension control, developed as an extension of an earlier standalone passive-suspension optimization study.

---

## Overview

This project models a 2-degree-of-freedom (2-DOF) quarter-car suspension system and evaluates three configurations under an identical road disturbance:

1. **Passive Baseline** — fixed, un-tuned suspension parameters
2. **Passive Optimized** — suspension parameters selected via grid search over a physically realistic range
3. **Active LQR** — passive baseline suspension augmented with an LQR state-feedback actuator

The goal is to quantify how much ride-comfort improvement (RMS body acceleration) is achievable through passive tuning alone versus active control, and to characterize the actuator-force cost of that additional improvement.

---

## System Model

### Physical Parameters

| Parameter | Symbol | Value |
|---|---|---|
| Unsprung mass (wheel/axle) | m1 | 40 kg |
| Sprung mass (body) | m2 | 400 kg |
| Suspension stiffness (baseline) | ks | 20,000 N/m |
| Suspension damping (baseline) | cs | 1,500 Ns/m |
| Tire stiffness | kt | 190,000 N/m |
| Tire damping | ct | 0 (neglected, standard simplification) |

### Equations of Motion (with active actuator force u)

```
m2·ẍs = -ks(xs - xu) - cs(ẋs - ẋu) + u
m1·ẍu =  ks(xs - xu) + cs(ẋs - ẋu) - kt(xu - xr) - u
```

State vector: **x = [xs, ẋs, xu, ẋu]ᵀ** (sprung position/velocity, unsprung position/velocity)

### State-Space Matrices

```
A = [   0        1        0       0   ]
    [ -50      -3.75     50      3.75 ]
    [   0        0        0       1   ]
    [  500      37.5    -5250   -37.5 ]

B = [   0    ]      (actuator force input)
    [ 0.0025 ]
    [   0    ]
    [ -0.025 ]

E = [  0   ]        (road disturbance input)
    [  0   ]
    [  0   ]
    [ 4750 ]
```

**Validation:** The A/E matrices were validated by running the state-space model open-loop (u = 0) and comparing RMS body acceleration against the full Simulink passive model under identical road input. Results agreed within ~2%, confirming the state-space formulation is a faithful representation of the Simulink plant.

### Road Input

Single bump disturbance: **0.05 m amplitude, from t = 1.36 s to t = 1.46 s.**

---

## Part 1: Passive Suspension Optimization

A 121-combination grid search was performed over suspension stiffness and damping, minimizing a weighted-sum performance index:

```
J = w1·(RMS_accel / RMS_accel_baseline)
  + w2·(RMS_travel / RMS_travel_baseline)
  + w3·(RMS_tire   / RMS_tire_baseline)

w1 = 0.60 (comfort), w2 = 0.25 (suspension travel), w3 = 0.15 (tire deflection)
```

**Search range:** Ks: 8,000–25,000 N/m, Cs: 600–2,000 Ns/m — bounded to physically realistic passenger-vehicle values based on published quarter-car literature.

### Methodology Note (Important)

Initial unconstrained sweeps showed the optimizer consistently favoring progressively softer suspension settings, with the optimum repeatedly landing on the lower boundary of the search range regardless of how far that boundary was extended. This is a known artifact of optimizing against a **single isolated bump** rather than continuous random road excitation: under an isolated disturbance, reduced sprung/unsprung coupling minimizes transmitted acceleration in a way that would **not** generalize to real-world stochastic road conditions (a suspension this soft would perform poorly under continuous excitation and would be impractical for ride-height and load-support reasons).

The search was therefore explicitly bounded to a realistic parameter range, and the reported optimum represents the best result within that bound — not an unconstrained global minimum. This test is best suited for **relative comparison between configurations** (passive vs. active), rather than as a standalone method for absolute suspension tuning.

### Results

| Performance Metric | Baseline (Ks=20,000, Cs=1,500) | Optimized (Ks=8,000, Cs=700) | % Change |
|---|---|---|---|
| RMS Body Acceleration | 1.5108 m/s² | 0.7812 m/s² | **48.29% improvement** |
| RMS Suspension Travel | 0.012511 m | 0.0108 m | **13.66% improvement** |
| RMS Tire Deflection | 0.0064032 m | 0.0072 m | 12.44% (trade-off, worse) |

---

## Part 2: Active LQR Suspension Control

An active force actuator was added between the sprung and unsprung masses (in parallel with the baseline passive Ks/Cs), controlled via linear-quadratic-regulator (LQR) state feedback: **u = -Kx**.

### Cost Function Design

Because RMS body acceleration (the target metric) is not itself a state variable, the LQR cost was built using an **output-weighted formulation** rather than weighting state velocity as a proxy:

```
z = Cz·x + Dz·u                    (z = ẍs, body acceleration)
Cz = [-ks/m2, -cs/m2, ks/m2, cs/m2] = [-50, -3.75, 50, 3.75]
Dz = 1/m2 = 0.0025

Q = qz·(Cz'·Cz) + Q_susp·(Csusp'·Csusp)     Csusp = [1, 0, -1, 0]  (suspension travel)
N = qz·(Cz'·Dz)
R = qz·(Dz²) + R0
```

A 125-combination sweep was performed over Q_acc (qz), Q_susp, and R0 values, evaluated against the same 0.05 m bump input. Results were additionally constrained by actuator force feasibility (see below).

### Selected Controller

```
Q_acc = 10,000   Q_susp = 1   R0 = 0.001

K_final = [-12572, 491, 15141, 937]
```

### Force-Constrained Selection

An unconstrained sweep found configurations with substantially lower RMS acceleration (down to ~0.042 m/s²), but these required peak actuator forces exceeding 6,000 N — unrealistic for a quarter-car actuator at this mass scale. A systematic scan across force ceilings (1,500 N–5,000 N) showed:

- **Below ~3,250 N peak force:** active control does **not** outperform the passive-optimized configuration.
- **At ~3,486 N peak force:** active control crosses over and outperforms passive optimization.

`K_final` was selected as the best-performing controller at this crossover force level — representing the point where active control first becomes worthwhile, given realistic actuator constraints.

### Validation

`K_final` was validated two ways:
1. **MATLAB linear state-space simulation** (`lsim` with closed-loop A - B·K)
2. **Full Simulink nonlinear block-diagram model**, with matching actuator sign convention and feedback gain polarity confirmed directly from the block diagram.

Time-history overlays of body acceleration from both methods matched closely across the full 10-second simulation (peak magnitude, timing, and decay envelope all consistent), confirming the state-space design and Simulink implementation are equivalent.

### Results — Three-Way Comparison

| Configuration | RMS Body Accel (m/s²) | RMS Susp Travel (m) | RMS Tire Deflection (m) | Peak Actuator Force (N) |
|---|---|---|---|---|
| Passive Baseline | 1.5108 | 0.012511 | 0.0064032 | — |
| Passive Optimized | 0.7812 | 0.0108 | 0.0072 | — |
| **Active LQR** | **0.70096** | 0.012562 | 0.0077201 | **3,486.4** |

**RMS control force:** 502.06 N

| Comparison | RMS Body Accel Reduction |
|---|---|
| Passive Optimized vs. Baseline | 48.3% |
| Active LQR vs. Passive Optimized | 10.3% |
| Active LQR vs. Baseline | 53.6% |

---

## Key Engineering Takeaways

1. **Passive optimization delivers the majority of the achievable comfort improvement** (48.3% of the total 53.6% gain) — active control adds a further, smaller increment (10.3% over the passive-optimized baseline).
2. **Active control's benefit is force-dependent, not unconditional.** Below ~3.5 kN of actuator capability, this LQR design does not outperform a well-tuned passive suspension — meaning the value of active control here is directly tied to actuator specification and cost, not a guaranteed win.
3. **Single-bump excitation has known limitations for suspension tuning.** It is well-suited for relative controller comparison (as used here) but is not representative of continuous real-world road input; a production tuning process would use stochastic road profiles.
4. **Output-weighted LQR cost formulation was necessary.** An initial attempt using state-velocity weighting as a proxy for acceleration produced a stable but ineffective controller; explicitly weighting the acceleration output (via Cz/Dz) was required to directly target the metric of interest.

---

## Requirements

- MATLAB (Control System Toolbox for `lqr`, `ss`, `lsim`)
- Simulink

## How to Run

1. Run `passive_baseline_optimization.m` to reproduce Part 1 results.
2. Run `lqr_gain_sweep.m` to reproduce the Q/R sweep and identify `K_final`.
3. Run `force_constraint_analysis.m` to reproduce the force-ceiling crossover analysis.
4. Open `QuarterCar_LQR.slx`, set the gain blocks to `K_final`, and run to validate against MATLAB results.
5. Run `three_way_comparison.m` to generate the final comparison table and plots.
