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

The model is implemented as a 2-DOF quarter-car system in MATLAB/Simulink.
