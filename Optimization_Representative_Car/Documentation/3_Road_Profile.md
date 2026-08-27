# Step 4 — Road Profile Development

## Overview

After implementing the 2-DOF quarter-car model in MATLAB Simulink, the next step was to develop the road profile used as the external disturbance to the suspension system.

The road profile provides the vertical input to the tire and allows the dynamic response of the sprung and unsprung masses to be evaluated.

---

## Road Disturbance

A controlled road bump was selected as the primary disturbance for the simulation.

The road profile was modified so that the main bump occurs at approximately:

$$
t \approx 1.36\;s
$$

This provides a clearly identifiable disturbance in the simulation and allows the transient response of the suspension system to be observed.

---

## Road Input

The road displacement is represented by:

$$
x_r(t)
$$

where:

- $x_r$ = road displacement
- $t$ = simulation time

The road displacement is applied as the input to the tire component of the quarter-car model.

The tire force is determined by the relative displacement between the unsprung mass and the road:

$$
F_t = K_t(x_1-x_r)
$$

where:

- $K_t$ = tire stiffness
- $x_1$ = unsprung mass displacement
- $x_r$ = road displacement

---

## Bump Location

The road profile was adjusted so that the primary bump occurs at approximately **1.36 seconds**.

This produces a distinct transient response in both the sprung and unsprung masses.

The resulting response can be observed through the displacement, velocity, and acceleration outputs of the model.

---

## Purpose of the Road Profile

A controlled road disturbance was used to provide a consistent input for evaluating suspension performance.

The same road profile is used for both the baseline and optimized suspension configurations.

This ensures that changes in the suspension response are caused by changes in the suspension parameters rather than changes in the road input.

---

## Road Profile Implementation

The road profile was implemented in MATLAB/Simulink and connected to the tire component of the 2-DOF quarter-car model.

The signal flow is:

```text
Road Profile
     ↓
Road Displacement xᵣ
     ↓
Tire
     ↓
Unsprung Mass
     ↓
Suspension
     ↓
Sprung Mass
     ↓
Vehicle Response
