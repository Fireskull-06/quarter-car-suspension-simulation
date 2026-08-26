# 2-DOF Quarter-Car Suspension System Simulation

## Overview

This project presents a **2-DOF quarter-car suspension system modeled and simulated using MATLAB/Simulink**. The model represents the vertical dynamics of a vehicle using two degrees of freedom: the **sprung mass** representing the vehicle body and the **unsprung mass** representing the wheel and associated components. A suspension spring-damper system connects the two masses, while the tyre is modeled using a tyre stiffness connected to the road input.

The model is subjected to a road disturbance to study the resulting vertical displacement of the sprung and unsprung masses.

## Objective

The objective of this project is to develop and simulate a 2-DOF quarter-car suspension model and analyze its response to a road disturbance using MATLAB/Simulink.

## System Description

The quarter-car model consists of:

* **Sprung mass (\(m_2\))** — represents the vehicle body supported by the suspension.
* **Unsprung mass (\(m_1\))** — represents the wheel, tyre, and other components below the suspension.
* **Suspension spring (\(k_s\))** — represents the stiffness of the vehicle suspension.
* **Suspension damper (\(c_s\))** — represents the damping provided by the suspension.
* **Tyre stiffness (\(k_t\))** — represents the vertical stiffness of the tyre.
* **Road input (\(y_r\))** — represents the disturbance experienced by the tyre.

The system is modeled using two coupled differential equations describing the vertical motion of the sprung and unsprung masses.

## System Parameters

| Parameter                     |   Value | Unit  |
| ----------------------------- | ------: | ----- |
| Sprung mass, \(m_2\)          |     450 | kg    |
| Unsprung mass, \(m_1\)        |      50 | kg    |
| Suspension stiffness, \(k s\) |  25,000 | N/m   |
| Suspension damping, \(c_s\)   |   1,000 | N·s/m |
| Tyre stiffness, \(k_t\)       | 190,000 | N/m   |

## Mathematical Model

The equation of motion for the sprung mass is:

$$
m_2\ddot{x}_2 =
-k_s(x_2-x_1)
-c_s(\dot{x}_2-\dot{x}_1)
$$

Therefore,

$$
\ddot{x}_2 =
\frac{-k_s(x_2-x_1)-c_s(\dot{x}_2-\dot{x}_1)}
{m_2}
$$

The equation of motion for the unsprung mass is:

$$
m_1\ddot{x}_1 =
k_s(x_2-x_1)
+c_s(\dot{x}_2-\dot{x}_1)
-k_t(x_1-y_r)
$$

Therefore,

$$
\ddot{x}_1 =
\frac{k_s(x_2-x_1)
+c_s(\dot{x}_2-\dot{x}_1)
-k_t(x_1-y_r)}
{m_1}
$$

where:

* \(x_2\) = displacement of the sprung mass
* \(x_1\) = displacement of the unsprung mass
* \(y_r\) = road displacement
* \(\dot{x}_1,\dot{x}_2\) = corresponding velocities
* \(\ddot{x}_1,\ddot{x}_2\) = corresponding accelerations

## Simulink Implementation

The mathematical equations are implemented in Simulink using:

* Sum blocks for calculating relative displacement and velocity
* Gain blocks for spring stiffness, damping, tyre stiffness, and inverse mass
* Integrator blocks for obtaining velocity and displacement from acceleration
* A Step block to provide the road disturbance
* Scope blocks for observing the system response

The model follows the physical force relationships between the sprung mass, unsprung mass, suspension, tyre, and road.

## Simulation

A road disturbance is applied as the input to the model. The resulting response of the sprung and unsprung masses is observed using the Simulink output.

The simulation is used to evaluate how the suspension system responds to road excitation and how the suspension and tyre characteristics influence the vehicle's vertical motion.

## Results

The simulation produces the expected response of the **2-DOF quarter-car suspension system** to the applied road disturbance. The sprung and unsprung masses exhibit different dynamic responses due to their different masses and the stiffness and damping characteristics of the suspension and tyre.

The obtained simulation response verifies the implementation of the mathematical model in Simulink.

### Simulation Output

*Add the final simulation graph here.*

Example:

```text
Results/
└── 2DOF_response.png
```

## 1-DOF to 2-DOF Development

This project extends the earlier **1-DOF quarter-car suspension model** by introducing an additional degree of freedom for the unsprung mass and explicitly modeling tyre stiffness.

The progression is:

**1-DOF Model → 2-DOF Model**

The 1-DOF model provides a simplified representation of vehicle suspension dynamics, while the 2-DOF model provides a more realistic representation by considering both body and wheel dynamics.

## Software Used

* **MATLAB**
* **Simulink**

## Future Scope

The model can be further extended by:

* Implementing PID or other suspension control strategies
* Comparing passive and active suspension systems
* Performing parameter optimization
* Studying different road profiles
* Analyzing suspension performance using additional performance metrics

## Conclusion

A 2-DOF quarter-car suspension system was successfully modeled and simulated using MATLAB/Simulink. The model incorporates sprung and unsprung masses, suspension spring and damper characteristics, tyre stiffness, and a road disturbance input. The simulation provides a foundation for further study of vehicle suspension dynamics and suspension control systems.

