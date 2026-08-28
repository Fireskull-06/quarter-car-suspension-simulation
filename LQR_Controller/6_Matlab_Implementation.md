## 6. MATLAB Implementation

The mathematical model is implemented in MATLAB before being transferred to the Simulink environment. The MATLAB implementation is used to define the quarter-car parameters, construct the state-space matrices, and verify the system dynamics.

### Define System Parameters

The physical parameters of the quarter-car model are first defined:

```matlab
m1 = 40;       % Unsprung mass (kg)
m2 = 400;      % Sprung mass (kg)

ks = 20000;    % Suspension stiffness (N/m)
cs = 1500;     % Suspension damping (Ns/m)
kt = 190000;   % Tire stiffness (N/m)
```

### Define State-Space Matrices

The state-space matrices are then constructed from the equations of motion:

```matlab
A = [0        1             0              0;
    -ks/m2   -cs/m2         ks/m2          cs/m2;
     0        0             0              1;
     ks/m1    cs/m1      -(ks+kt)/m1      -cs/m1];

B = [0;
     1/m2;
     0;
    -1/m1];

E = [0;
     0;
     0;
     kt/m1];
```

The resulting model has four states corresponding to the displacement and velocity of the sprung and unsprung masses.

### State Vector

The state vector used throughout the MATLAB and Simulink implementation is:

```text
x = [z2  z2_dot  z1  z1_dot]^T
```

The state-space model is therefore:

```text
x_dot = A*x + B*u + E*z0
```

where the control input `u` represents the active suspension actuator force and `z0` represents the road disturbance.

### System Stability

Before designing the controller, the open-loop system is checked by calculating its eigenvalues:

```matlab
eig(A)
```

The eigenvalues are used to verify the dynamic characteristics of the passive suspension system.

### MATLAB Simulation

MATLAB is also used to simulate the state-space model and calculate suspension performance metrics. The main metrics used in this project are:

- RMS body acceleration
- RMS suspension travel
- RMS tire deflection

These metrics provide a quantitative basis for comparing the passive suspension with the LQR-controlled active suspension.

The MATLAB model therefore serves as the foundation for controller development and provides an independent way to verify the results obtained from the Simulink implementation.
