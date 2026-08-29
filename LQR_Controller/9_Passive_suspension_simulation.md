## 9. Passive Suspension Simulation

Before introducing the LQR controller, the quarter-car model is evaluated as a passive suspension system. This simulation establishes the baseline performance against which the active suspension is later compared.

For the passive configuration, the active actuator is disabled:

```text
u = 0
```

The suspension therefore operates only through the mechanical elements defined in the model:

- Suspension spring
- Suspension damper
- Tire stiffness
- Sprung mass
- Unsprung mass

### Simulation Conditions

The passive suspension is simulated using the same system parameters and road profile defined in the previous sections.

The simulation uses:

- Simulation duration = 10 s
- Sampling time = 0.005 s
- Road bump height = 0.05 m
- Bump start time = 1.36 s
- Bump end time = 1.46 s

The resulting suspension response is recorded using the Simulink `To Workspace` block.

### Output Signals

Three primary performance signals are extracted from the simulation:

1. Body acceleration
2. Suspension travel
3. Tire deflection

These outputs are used to evaluate ride comfort and suspension performance.

The suspension travel is defined as the relative displacement between the sprung and unsprung masses:

```text
Suspension travel = z2 - z1
```

The tire deflection is defined as the relative displacement between the unsprung mass and the road:

```text
Tire deflection = z1 - z0
```

Body acceleration is obtained from the acceleration of the sprung mass.

### MATLAB RMS Calculation

The RMS values of the recorded signals are calculated in MATLAB:

```matlab
RMS_body_accel_passive = rms(body_accel);
RMS_susp_travel_passive = rms(susp_travel);
RMS_tire_deflection_passive = rms(tire_deflection);
```

The passive suspension provides the reference values required to quantify the improvement achieved by the LQR-controlled active suspension.

### Passive Baseline Results

The final passive simulation produced the following RMS values:

| Performance Metric | Passive Suspension |
|---|---:|
| RMS body acceleration | 1.5108 m/s² |
| RMS suspension travel | 0.0125 m |
| RMS tire deflection | 0.0064 m |

These values are used as the baseline for the active suspension evaluation in the subsequent sections.
