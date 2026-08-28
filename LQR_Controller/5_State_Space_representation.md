## 5. State-Space Representation

To design the LQR controller, the quarter-car equations are converted into a state-space representation.

The state vector is defined as:

```text
x = [z2  z2_dot  z1  z1_dot]^T
```

where:

- z2 = sprung-mass displacement
- z2_dot = sprung-mass velocity
- z1 = unsprung-mass displacement
- z1_dot = unsprung-mass velocity

The system is represented in the form:

```text
x_dot = A*x + B*u + E*z0
```

where:

- A = system state matrix
- B = control input matrix
- E = road disturbance matrix
- u = active suspension actuator force
- z0 = road displacement

### System Matrices

Using the equations of motion developed in the previous section, the state-space matrices are:

```text
A = [  0          1             0              0
      -Ks/m2     -Cs/m2         Ks/m2          Cs/m2
       0          0             0              1
       Ks/m1      Cs/m1      -(Ks+Kt)/m1      -Cs/m1 ]
```

The control input matrix is:

```text
B = [ 0
      1/m2
      0
     -1/m1 ]
```

The road disturbance matrix is:

```text
E = [ 0
      0
      0
      Kt/m1 ]
```

The complete system therefore becomes:

```text
x_dot = A*x + B*u + E*z0
```

This representation separates the effects of the active actuator force from the road disturbance, allowing the system to be analyzed and controlled using state-space methods.

### MATLAB Implementation

The state-space matrices are implemented in MATLAB using the physical parameters defined previously:

```matlab
A = [0        1             0              0;
    -Ks/m2   -Cs/m2         Ks/m2          Cs/m2;
     0        0             0              1;
     Ks/m1    Cs/m1      -(Ks+Kt)/m1      -Cs/m1];

B = [0;
     1/m2;
     0;
    -1/m1];

E = [0;
     0;
     0;
     Kt/m1];
```

The state-space model is then used as the mathematical representation of the quarter-car suspension system for subsequent analysis and LQR controller design.
