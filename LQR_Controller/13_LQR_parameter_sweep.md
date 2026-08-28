## 13. Systematic LQR Parameter Sweep

To identify a suitable LQR controller, a systematic parameter sweep was performed over different combinations of `Q_acc`, `Q_susp`, and `R`.

For each combination, the LQR gain matrix was calculated and the resulting closed-loop system was evaluated using the same road disturbance.

The following performance metrics were recorded for each controller:

- RMS body acceleration
- RMS suspension travel
- RMS tire deflection
- RMS control force
- Peak control force

### Parameter Ranges

The values investigated were:

```text
Q_acc  = [10, 100, 1000, 10000]
Q_susp = [1, 10, 100, 1000, 10000]
R      = [1e-5, 1e-4, 1e-3, 1e-2]
```

This produced a range of LQR controllers with different trade-offs between ride comfort and actuator effort.

### Representative Sweep Results

Some of the best-performing combinations from the parameter sweep are shown below:

| Q_acc | Q_susp | R | RMS Body Acceleration (m/s²) | RMS Suspension Travel (m) | RMS Tire Deflection (m) | RMS Control Force (N) | Peak Control Force (N) |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 10000 | 1 | 1e-05 | 0.04199 | 0.01656 | 0.01309 | 1329 | 6155.5 |
| 10000 | 10000 | 1e-05 | 0.04374 | 0.01654 | 0.01306 | 1325.4 | 6150.9 |
| 10000 | 1 | 0.0001 | 0.12014 | 0.01562 | 0.01190 | 1174.2 | 5930.7 |
| 10000 | 1 | 0.01 | 0.70097 | 0.01256 | 0.00772 | 502.06 | 3486.4 |
| 1000 | 1 | 0.001 | 0.70097 | 0.01256 | 0.00772 | 502.06 | 3486.4 |
| 100 | 1 | 0.0001 | 0.70097 | 0.01256 | 0.00772 | 502.06 | 3486.4 |

### Trade-Off Analysis

The sweep demonstrates the trade-off between ride comfort and actuator effort.

Very small values of `R` allow the controller to use greater actuator force and can produce extremely low body acceleration. However, this also results in larger suspension and tire responses and significantly higher peak actuator force.

Increasing `R` reduces actuator demand but results in a less aggressive controller and a higher RMS body acceleration.

For example:

```text
R = 1e-5  → RMS body acceleration = 0.04199 m/s²
             Peak control force     = 6155.5 N

R = 0.01  → RMS body acceleration = 0.70097 m/s²
             Peak control force     = 3486.4 N
```

The controller with `R = 0.01` was selected as a practical compromise because it provides a substantial reduction in body acceleration while keeping the peak control force below 3.5 kN.

### Selected LQR Weights

The final weighting parameters selected for further simulation were:

```text
Q_acc  = 10000
Q_susp = 1
R      = 0.01
```

These values were then used to calculate the final LQR feedback gain and implement the controller in Simulink.
