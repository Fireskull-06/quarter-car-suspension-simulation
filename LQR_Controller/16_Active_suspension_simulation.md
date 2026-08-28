## 16. Active Suspension Simulation

After verifying the stability of the final LQR controller, the controller was implemented in the Simulink quarter-car model and evaluated under the same road disturbance used for the passive suspension simulation.

The purpose of this simulation is to determine how the active suspension responds to the road bump and to quantify the improvement obtained through LQR control.

### Simulation Configuration

The active suspension simulation uses the same physical parameters and road profile as the passive baseline.

```text
Simulation duration = 2 s
Sampling time       = 0.005 s
Bump height         = 0.05 m
Bump start time     = 1.36 s
Bump end time       = 1.46 s
```

The final LQR controller is implemented using:

```text
K_final = [-12572  491  15141  937]
```

with the control law:

```text
u = -K_final*x
```

### Active Suspension Outputs

The Simulink model records the following quantities:

- Body acceleration
- Suspension travel
- Tire deflection
- Actuator force

The first three outputs are used to evaluate suspension performance, while the actuator force is used to assess the control effort required by the LQR controller.

### RMS Performance

The RMS values are calculated from the simulated output signals:

```matlab
RMS_body_accel_LQR = rms(body_accel);
RMS_susp_travel_LQR = rms(susp_travel);
RMS_tire_deflection_LQR = rms(tire_deflection);
```

The final active suspension simulation produced:

| Performance Metric | LQR Active Suspension |
|---|---:|
| RMS body acceleration | 0.5528 m/s² |
| RMS suspension travel | 0.0096 m |
| RMS tire deflection | 0.0067 m |

The RMS body acceleration is substantially lower than the passive baseline, indicating a significant improvement in ride comfort.

The active suspension results are compared directly with the passive suspension results in the following section.
