## 12. LQR Weight Selection

The performance of an LQR controller depends strongly on the choice of the weighting matrices. The weights were therefore varied systematically rather than selecting a single combination arbitrarily.

The controller uses the quadratic cost function:

```text
J = integral (x^T*Q*x + u^T*R*u) dt
```

The weighting parameters considered during the controller design were:

- `Q_acc` = weighting applied to body acceleration
- `Q_susp` = weighting applied to suspension travel
- `R` = weighting applied to actuator effort

### Acceleration Weighting

Body acceleration is the primary ride-comfort metric in this project. Therefore, increasing `Q_acc` increases the penalty associated with body acceleration and encourages the controller to reduce it.

### Suspension Travel Weighting

`Q_susp` is used to penalize excessive suspension travel. Increasing this weighting encourages the controller to keep the relative displacement between the sprung and unsprung masses smaller.

### Control Effort Weighting

`R` penalizes the actuator force. A smaller value of `R` allows the controller to apply greater control effort, while a larger value of `R` produces a more conservative controller with lower actuator demand.

### Parameter Sweep

Instead of relying on a single trial-and-error selection, multiple combinations of `Q_acc`, `Q_susp`, and `R` were evaluated.

For each combination, the following quantities were recorded:

- RMS body acceleration
- RMS suspension travel
- RMS tire deflection
- RMS control force
- Peak control force

A representative MATLAB implementation of the sweep is:

```matlab
Q_acc_values = [10 100 1000 10000];
Q_susp_values = [1 10 100 1000 10000];
R_values = [1e-5 1e-4 1e-3 1e-2];
```

For each combination, the LQR controller was calculated and the resulting closed-loop system was simulated.

### Controller Selection

The objective was not simply to minimize body acceleration. The controller also needed to maintain reasonable suspension and tire behavior while avoiding excessive actuator force.

The parameter sweep identified the following candidate as a suitable compromise:

```text
Q_acc  = 10000
Q_susp = 1
R      = 0.01
```

This configuration provided a substantial reduction in body acceleration while keeping the peak control force below 3.5 kN.

The detailed sweep results and final controller selection are presented in the following sections.
