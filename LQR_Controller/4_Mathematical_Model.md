## 4. Mathematical Model

The quarter-car system is modeled using two degrees of freedom: the vertical motion of the sprung mass and the vertical motion of the unsprung mass.

The variables used in the model are:

- z2 = sprung-mass displacement
- z2_dot = sprung-mass velocity
- z1 = unsprung-mass displacement
- z1_dot = unsprung-mass velocity
- z0 = road displacement
- u = active suspension actuator force

### Sprung Mass Equation

The sprung mass is affected by the suspension spring, suspension damper, and active actuator force.

```text
m2*z2_ddot = -Ks*(z2 - z1) - Cs*(z2_dot - z1_dot) + u
```

### Unsprung Mass Equation

The unsprung mass is affected by the suspension spring, suspension damper, tire force, and actuator reaction force.

```text
m1*z1_ddot = Ks*(z2 - z1) + Cs*(z2_dot - z1_dot) - Kt*(z1 - z0) - u
```

where z0 represents the vertical displacement of the road surface.

### Passive Suspension

For the passive suspension model, there is no active actuator force:

```text
u = 0
```

Therefore, the passive system contains only the suspension spring, suspension damper, and tire stiffness.

The passive suspension serves as the baseline against which the performance of the active suspension is evaluated.

### Active Suspension

For the active suspension model, an actuator is introduced between the sprung and unsprung masses. The actuator force is determined using state feedback:

```text
u = -K*x
```

where:

- K = LQR feedback gain matrix
- x = system state vector
- u = actuator force

The state-feedback controller uses the measured or estimated states of the quarter-car system to generate an actuator force that modifies the suspension response.

### Model Representation

The equations above describe the physical dynamics of the quarter-car suspension. They are subsequently converted into state-space form for MATLAB analysis and LQR controller design.

The resulting model allows the passive suspension response to be compared with the controlled active suspension response under the same road disturbance.
