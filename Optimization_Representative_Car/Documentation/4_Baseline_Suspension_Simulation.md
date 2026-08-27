# Step 4 — Baseline Suspension Simulation

## Overview

After establishing the 2-DOF quarter-car model and the road profile, the next step was to run the **baseline suspension simulation**.

The purpose of the baseline simulation was to establish the initial performance of the suspension system before any optimization was performed.

The baseline results provide a reference against which the optimized suspension configuration can later be compared.

---

## Baseline Parameters

The baseline simulation was performed using the original suspension parameters established in Step 1.

| Parameter | Symbol | Value | Unit |
|---|---:|---:|---|
| Unsprung mass | $m_1$ | 40 | kg |
| Sprung mass | $m_2$ | 400 | kg |
| Suspension stiffness | $K_s$ | 20,000 | N/m |
| Suspension damping | $C_s$ | 1,500 | Ns/m |
| Tire stiffness | $K_t$ | 190,000 | N/m |

The vehicle masses and tire stiffness were kept constant during the subsequent optimization process.

---

## Simulation Setup

The baseline parameters were entered into the 2-DOF Simulink model developed in Step 3.

The road profile developed in Step 4 was then applied as the external disturbance.

The main bump in the road profile occurs at approximately:

$$
t \approx 1.36\;s
$$

The same road input was used throughout the analysis to ensure a consistent basis for comparison.

---

## Baseline Simulation

The model was simulated using:

$$
K_s = 20,000\;N/m
$$

$$
C_s = 1,500\;Ns/m
$$

The simulation produced the dynamic response of the sprung and unsprung masses to the road disturbance.

The resulting outputs were recorded for further performance analysis.

---

## Observed System Response

The baseline simulation was used to observe:

- Sprung mass displacement
- Unsprung mass displacement
- Sprung mass velocity
- Unsprung mass velocity
- Sprung mass acceleration
- Suspension travel
- Tire deflection

The response following the road disturbance provides the basis for evaluating the behavior of the baseline suspension system.

---

## Simulation Output

The resulting simulation output was recorded from the Simulink model.

![Baseline Simulation Output](images/2DOF_Output.png)

The output shows the response of the quarter-car system following the road disturbance.

The recorded signals were subsequently used to calculate quantitative performance metrics for the suspension.

---

## Performance Evaluation

Three primary metrics were selected to evaluate the baseline suspension:

### RMS Body Acceleration

Used to evaluate the vibration experienced by the vehicle body and provide an indication of ride comfort.

### RMS Suspension Travel

Used to evaluate the relative movement between the sprung and unsprung masses.

$$
x_{travel} = x_2 - x_1
$$

### RMS Tire Deflection

Used to evaluate the relative movement between the tire and the road.

$$
x_{tire} = x_1 - x_r
$$

These metrics were calculated from the simulation data and used to establish the baseline performance of the suspension.

---

## Outcome of Step 5

The baseline 2-DOF suspension simulation was successfully completed using the original suspension stiffness and damping values.

The resulting simulation data established the **baseline performance reference** required for the subsequent optimization stage.

The next step was to calculate and analyze the RMS performance metrics obtained from the baseline simulation.
