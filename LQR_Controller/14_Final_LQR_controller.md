## 14. Final LQR Controller

Based on the parameter sweep, the selected LQR weighting parameters were:

```text
Q_acc  = 10000
Q_susp = 1
R      = 0.01
```

These weights were selected to provide a balance between reducing body acceleration, limiting suspension travel, and controlling actuator effort.

### Final LQR Gain

Using the selected weights, the LQR gain was calculated in MATLAB as:

```matlab
K_final = lqr(A,B,Q_total,R_total,N_total);
```

The resulting gain matrix was:

```text
K_final = [-12572  491  15141  937]
```

The active suspension control law is therefore:

```text
u = -K_final*x
```

where:

```text
x = [z2  z2_dot  z1  z1_dot]^T
```

### Simulink Implementation

The state-feedback controller was implemented in Simulink using the four system states.

Because the controller follows:

```text
u = -K*x
```

the corresponding feedback gains used in the Simulink model were:

```text
z2      →  12572
z2_dot  →  -491
z1      →  -15141
z1_dot  →  -937
```

The resulting actuator force is fed back into the quarter-car model between the sprung and unsprung masses.

### Final Controller Configuration

The final controller configuration used for the active suspension simulation is:

| Parameter | Value |
|---|---:|
| Q_acc | 10000 |
| Q_susp | 1 |
| R | 0.01 |
| K1 | -12572 |
| K2 | 491 |
| K3 | 15141 |
| K4 | 937 |

This controller is used for the final active suspension simulation and passive-versus-active performance comparison.
