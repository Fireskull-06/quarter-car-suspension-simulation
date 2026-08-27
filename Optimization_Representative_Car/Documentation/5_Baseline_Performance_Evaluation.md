# Step 5 — Baseline Performance Evaluation

## Overview

After completing the baseline simulation, the next step was to quantify the performance of the suspension system using the simulation data.

Three performance metrics were selected to evaluate the baseline suspension:

1. RMS Body Acceleration
2. RMS Suspension Travel
3. RMS Tire Deflection

These metrics provide a quantitative basis for evaluating the suspension and later comparing the baseline configuration with the optimized configuration.

---

## 1. RMS Body Acceleration

RMS body acceleration was used as the primary measure of **ride comfort**.

The vertical acceleration of the sprung mass was obtained from the simulation output.

The RMS value was calculated as:

$$
a_{RMS} =
\sqrt{
\frac{1}{T}
\int_0^T a_s^2(t)\,dt
}
$$

where:

- $a_s(t)$ = sprung mass acceleration
- $T$ = total simulation time

A lower RMS body acceleration indicates lower overall vibration transmitted to the vehicle body.

---

## 2. RMS Suspension Travel

Suspension travel represents the relative displacement between the sprung and unsprung masses.

It was calculated as:

$$
x_{travel} = x_2 - x_1
$$

The RMS suspension travel was then calculated as:

$$
x_{travel,RMS} =
\sqrt{
\frac{1}{T}
\int_0^T
(x_2-x_1)^2\,dt
}
$$

where:

- $x_2$ = sprung mass displacement
- $x_1$ = unsprung mass displacement

Lower suspension travel generally indicates reduced relative movement between the vehicle body and wheel assembly.

---

## 3. RMS Tire Deflection

Tire deflection represents the relative displacement between the unsprung mass and the road.

It was calculated as:

$$
x_{tire} = x_1-x_r
$$

The RMS tire deflection was calculated as:

$$
x_{tire,RMS} =
\sqrt{
\frac{1}{T}
\int_0^T
(x_1-x_r)^2\,dt
}
$$

where:

- $x_1$ = unsprung mass displacement
- $x_r$ = road displacement

This metric provides an indication of how effectively the tire follows the road input.

---

## Baseline Results

The baseline suspension configuration was:

$$
K_s = 20,000\;N/m
$$

$$
C_s = 1,500\;Ns/m
$$

The RMS performance values obtained from the baseline simulation were recorded as follows:

| Performance Metric | Baseline Value | Unit |
|---|---:|---|
| RMS Body Acceleration | **1.1652** | m/s² |
| RMS Suspension Travel | **0.0104** | m |
| RMS Tire Deflection | **0.0062** | m |

These values represent the performance of the original baseline configuration.

---

## Why These Metrics Were Selected

The three metrics were selected because suspension performance involves multiple competing objectives.

### Ride Comfort

RMS body acceleration indicates the magnitude of vibration experienced by the vehicle body.

### Suspension Movement

RMS suspension travel indicates how much relative movement occurs within the suspension system.

### Tire Behavior

RMS tire deflection indicates the vertical deformation required for the tire to follow the road disturbance.

Considering all three metrics prevents the optimization from focusing exclusively on ride comfort while ignoring suspension movement or tire behavior.

---

## Baseline as the Reference Configuration

The baseline results serve as the reference point for the optimization stage.

The optimization process modifies the suspension parameters while maintaining the same:

- Vehicle masses
- Tire stiffness
- Road profile
- Simulation conditions

This allows the effect of changing the suspension stiffness and damping to be evaluated objectively.

---

## Outcome of Step 6

The baseline suspension performance was quantified using RMS body acceleration, RMS suspension travel, and RMS tire deflection.

These metrics established the reference performance against which the optimized suspension configuration was evaluated.

The next step was to perform **suspension parameter optimization** to determine improved values of suspension stiffness and damping.
