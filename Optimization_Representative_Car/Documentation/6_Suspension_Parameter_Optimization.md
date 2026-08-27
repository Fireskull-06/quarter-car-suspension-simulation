# Step 6 — Suspension Parameter Optimization

## Overview

After establishing the baseline performance, the next step was to optimize the suspension parameters.

The optimization focused on the two suspension parameters that directly influence the dynamic response of the quarter-car model:

- Suspension stiffness, $K_s$
- Suspension damping, $C_s$

The vehicle masses and tire stiffness were kept constant during the optimization.

---

## Baseline Configuration

The initial suspension configuration used for the baseline simulation was:

$$
K_s = 20,000\;N/m
$$

$$
C_s = 1,500\;Ns/m
$$

These values were used as the reference configuration for evaluating the effect of changing the suspension parameters.

---

## Optimization Objectives

The optimization was performed with the objective of improving the overall suspension performance.

The three performance metrics considered were:

1. **RMS Body Acceleration** — indicator of ride comfort
2. **RMS Suspension Travel** — indicator of suspension movement
3. **RMS Tire Deflection** — indicator of tire-road response

Since these performance measures can have competing requirements, the optimization was treated as a multi-objective performance problem.

The goal was not simply to minimize one individual metric, but to obtain a better overall balance between the three.

---

## Parameters Varied

The suspension stiffness and damping were varied while maintaining the remaining model parameters constant.

| Parameter | Baseline Value | Optimized Value | Unit |
|---|---:|---:|---|
| Suspension stiffness | $K_s = 20,000$ | **$K_s = 15,000$** | N/m |
| Suspension damping | $C_s = 1,500$ | **$C_s = 600$** | Ns/m |

The following parameters remained unchanged:

| Parameter | Value | Unit |
|---|---:|---|
| Unsprung mass, $m_1$ | 40 | kg |
| Sprung mass, $m_2$ | 400 | kg |
| Tire stiffness, $K_t$ | 190,000 | N/m |

---

## Optimization Process

The optimization followed the general process:

```text
Baseline Parameters
        ↓
Run 2-DOF Simulation
        ↓
Calculate Performance Metrics
        ↓
Modify Kₛ and Cₛ
        ↓
Run Simulation
        ↓
Evaluate Performance
        ↓
Compare Results
        ↓
Select Improved Parameter Combination
