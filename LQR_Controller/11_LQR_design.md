## 11. LQR Controller Design

After establishing the passive suspension baseline, an active suspension controller is designed using the Linear Quadratic Regulator (LQR) method.

LQR is a state-feedback control technique that determines the control input by minimizing a cost function associated with the system states and control effort.

### State Feedback

The controller uses the four states of the quarter-car model:

```text
x = [z2  z2_dot  z1  z1_dot]^T
```

The control force is calculated as:

```text
u = -K*x
```

where:

- K = LQR feedback gain matrix
- x = system state vector
- u = actuator force

The LQR controller therefore continuously adjusts the actuator force according to the current state of the suspension system.

### LQR Cost Function

The controller minimizes the quadratic cost function:

```text
J = integral (x^T*Q*x + u^T*R*u) dt
```

where:

- Q = state weighting matrix
- R = control effort weighting
- J = total performance cost

The matrix Q determines how strongly the system states are penalized, while R determines how strongly the controller penalizes actuator effort.

A higher state weighting encourages the controller to reduce the corresponding state response, while a higher value of R discourages large actuator forces.

### State Weighting

For this project, the LQR design places particular emphasis on reducing body acceleration because ride comfort is the primary performance objective.

The suspension behavior is also considered to prevent excessive suspension motion.

The weighting matrices are therefore constructed based on the desired performance outputs rather than assigning arbitrary weights to individual states.

### MATLAB LQR Implementation

The LQR controller is implemented in MATLAB using the state-space model:

```matlab
K = lqr(A,B,Q,R,N);
```

where `Q`, `R`, and `N` define the LQR cost function and `K` is the resulting state-feedback gain matrix.

The resulting controller is then implemented in Simulink using the state-feedback relationship:

```text
u = -K*x
```

The LQR controller is subsequently evaluated using the same road disturbance used for the passive suspension simulation.
