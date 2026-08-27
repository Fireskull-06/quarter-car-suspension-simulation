# Step 2 — 2-DOF Simulink Model Implementation

## Overview

After establishing the baseline parameters and developing the mathematical equations of motion, the next step was to implement the **2-DOF quarter-car suspension system in MATLAB Simulink**.

The purpose of this step was to convert the mathematical model into a dynamic simulation model that could be subjected to a road disturbance and used to evaluate suspension performance.

---

## Model Structure

The 2-DOF system consists of two masses connected through the suspension system.

```text
                  Sprung Mass
                    m₂
                     │
                     │
              ┌──────┴──────┐
              │             │
        Suspension       Suspension
          Spring           Damper
            Kₛ               Cₛ
              │             │
              └──────┬──────┘
                     │
                Unsprung Mass
                     m₁
                     │
                     │
                 Tire Spring
                     Kₜ
                     │
                     │
                 Road Input
                     xᵣ
```

The **sprung mass \(m_2\)** represents the vehicle body, while the **unsprung mass \(m_1\)** represents the wheel and associated components.

The suspension spring and damper connect the two masses, while the tire stiffness connects the unsprung mass to the road input.

---

## Simulink Implementation

The equations of motion developed in the previous step were implemented using standard Simulink blocks.

The model contains:

* **Sum blocks** to calculate the relative displacement and velocity between the sprung and unsprung masses.
* **Gain blocks** to represent suspension stiffness, damping, tire stiffness, and mass values.
* **Integrator blocks** to obtain velocity and displacement from acceleration.
* **Feedback connections** to represent the interaction between the sprung and unsprung masses.
* **Road input** to introduce the external disturbance.
* **Output blocks** to record the resulting suspension response.

---

## Force Calculation

The suspension force is determined by the relative displacement and relative velocity between the sprung and unsprung masses.

$$
F_s = K_s(x_2-x_1)+C_s(\dot{x}_2-\dot{x}_1)
$$

The tire force is determined by the relative displacement between the unsprung mass and the road.

$$
F_t = K_t(x_1-x_r)
$$

These forces are used to calculate the accelerations of the sprung and unsprung masses.

---

## Integration of the Equations

The calculated acceleration of each mass is passed through two integration stages.

For each mass:

$$
Acceleration \rightarrow Velocity \rightarrow Displacement
$$

This allows the Simulink model to continuously calculate the position and velocity of both the sprung and unsprung masses throughout the simulation.

---

## Model Parameters

The baseline parameters established in Step 1 were entered into the Simulink model:

| Parameter            |  Symbol |   Value | Unit |
| -------------------- | ------: | ------: | ---- |
| Unsprung mass        | \(m₁) |      40 | kg   |
| Sprung mass          | \(m₂) |     400 | kg   |
| Suspension stiffness | \(Kₛ) |  20,000 | N/m  |
| Suspension damping   | \(Cₛ) |   1,500 | Ns/m |
| Tire stiffness       | \(Kₜ) | 190,000 | N/m  |

These values define the initial baseline configuration of the suspension system.

---

## Simulink Model

The completed block diagram represents the coupled dynamics of the two-degree-of-freedom quarter-car system.

The model was subsequently used to introduce a controlled road disturbance and evaluate the resulting vehicle response.

---

## Outcome of Step 3

At the end of this step, a functional **2-DOF quarter-car suspension model** was established in MATLAB Simulink.

The model was ready for the next stage:

> **Introducing and configuring the road disturbance for the suspension simulation.**
