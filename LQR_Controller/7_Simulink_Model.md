## 7. Simulink Model

After developing and verifying the mathematical model in MATLAB, the quarter-car suspension system is implemented in MATLAB Simulink. Simulink provides a block-based representation of the suspension dynamics and allows the passive and active suspension configurations to be simulated under the same road disturbance.

### Model Structure

The Simulink model represents the physical components of the quarter-car system using the following elements:

- Sprung mass
- Unsprung mass
- Suspension spring
- Suspension damper
- Tire stiffness
- Road input
- Active suspension actuator
- State-feedback controller
- Output measurement blocks

The sprung and unsprung masses are modeled using their respective equations of motion. The suspension spring and damper act between the two masses, while the tire stiffness connects the unsprung mass to the road input.

### Passive Suspension Configuration

The passive suspension is first simulated without an active actuator.

```text
u = 0
```

This configuration establishes the baseline response of the suspension system.

The passive model is subjected to the defined road disturbance, and the resulting body acceleration, suspension travel, and tire deflection are recorded for performance evaluation.

### Active Suspension Configuration

The passive model is then extended by introducing an active actuator between the sprung and unsprung masses.

The actuator force is generated using state feedback:

```text
u = -K*x
```

The four system states are fed back to the controller:

```text
x = [z2  z2_dot  z1  z1_dot]^T
```

The controller therefore uses the displacement and velocity of both the sprung and unsprung masses to calculate the required actuator force.

### Simulink Signal Flow

The overall signal flow of the active suspension model is:

```text
Road Input
    |
    v
Unsprung Mass <---- Tire
    |
    | Suspension Spring + Damper
    v
Sprung Mass
    |
    v
System States
    |
    v
LQR State Feedback
    |
    v
Actuator Force
    |
    +----> Suspension System
```

The feedback loop allows the actuator to respond dynamically to changes in the suspension states caused by the road disturbance.

### Output Measurements

The Simulink model records the following quantities:

- Body acceleration
- Suspension travel
- Tire deflection
- Actuator force

These outputs are transferred to the MATLAB workspace using `To Workspace` blocks.

The recorded signals are subsequently used to calculate RMS performance metrics and compare the passive and LQR-controlled suspension systems.

### Simulation Setup

The same vehicle parameters and road profile are used for both passive and active simulations. This ensures that any change in performance is attributable to the LQR controller rather than a change in the physical model or road input.

The Simulink model therefore provides the final simulation environment in which the passive suspension and active LQR suspension are evaluated under identical operating conditions.
