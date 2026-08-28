# Quarter-Car Suspension Modeling and LQR Control

This project develops and analyzes a quarter-car suspension model using MATLAB and Simulink. The model is first evaluated as a passive suspension system and is then extended with an active suspension controller based on Linear Quadratic Regulator (LQR) state feedback.

The project investigates the response of the vehicle suspension to a road disturbance and compares passive and active suspension performance using RMS body acceleration, suspension travel, and tire deflection.

The objective is to determine whether active suspension control can improve ride comfort while maintaining acceptable suspension and tire behavior.

## Objectives

- Develop a quarter-car suspension model in MATLAB/Simulink.
- Model the vehicle suspension as a 2-DOF system.
- Formulate the system in state-space form.
- Analyze the response of the passive suspension to a road disturbance.
- Design an LQR-based active suspension controller.
- Evaluate closed-loop stability using the system eigenvalues.
- Compare passive and active suspension performance using RMS metrics.
- Analyze the trade-off between ride comfort, suspension travel, tire deflection, and actuator effort.

## 2. Vehicle / Suspension Model

A quarter-car model is used to represent the vertical dynamics of one wheel and one quarter of the vehicle body. The model separates the vehicle into two main masses:

- **Sprung mass:** represents one quarter of the vehicle body.
- **Unsprung mass:** represents the wheel, tire, and associated suspension components.

The sprung and unsprung masses are connected through the suspension spring and damper. The tire connects the unsprung mass to the road surface and is modeled as a spring.

The model uses two degrees of freedom:

1. Vertical displacement of the sprung mass.
2. Vertical displacement of the unsprung mass.

An active suspension actuator is subsequently introduced between the sprung and unsprung masses. The actuator force is controlled using an LQR state-feedback controller.

### Physical Elements

| Element | Representation |
|---|---|
| Sprung mass | Vehicle body |
| Unsprung mass | Wheel and associated components |
| Suspension spring | Spring stiffness between sprung and unsprung masses |
| Suspension damper | Damping between sprung and unsprung masses |
| Tire | Tire stiffness between unsprung mass and road |
| Road input | Vertical road displacement |
| Actuator | Active suspension force |

## 3. System Parameters

| Parameter | Symbol | Value | Unit |
|---|---|---:|---|
| Sprung mass | m2 | 400 | kg |
| Unsprung mass | m1 | 40 | kg |
| Suspension stiffness | Ks | 20,000 | N/m |
| Suspension damping | Cs | 1,500 | Ns/m |
| Tire stiffness | Kt | 190,000 | N/m |

The model therefore represents a vehicle quarter with a total modeled mass of 440 kg.

## 4. Mathematical Model

The variables used are:

- z2 = sprung-mass displacement
- z2_dot = sprung-mass velocity
- z1 = unsprung-mass displacement
- z1_dot = unsprung-mass velocity
- z0 = road displacement
- u = active suspension actuator force

### Sprung Mass Equation

```text
m2*z2_ddot = -Ks*(z2 - z1) - Cs*(z2_dot - z1_dot) + u
