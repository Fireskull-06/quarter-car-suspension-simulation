## 10. Passive Suspension Performance Metrics

The passive suspension simulation provides the baseline performance against which the LQR-controlled active suspension is evaluated.

Three primary performance metrics are used to quantify the response of the suspension:

### RMS Body Acceleration

RMS body acceleration is used as the primary measure of ride comfort. A lower RMS body acceleration indicates that less vibration is transmitted to the vehicle body.

```text
RMS_body_accel = rms(body_accel)
```

The passive suspension produced:

```text
RMS body acceleration = 1.5108 m/s^2
```

### RMS Suspension Travel

Suspension travel represents the relative movement between the sprung and unsprung masses.

```text
Suspension travel = z2 - z1
```

The RMS value is calculated as:

```text
RMS_susp_travel = rms(susp_travel)
```

The passive suspension produced:

```text
RMS suspension travel = 0.0125 m
```

### RMS Tire Deflection

Tire deflection represents the relative displacement between the unsprung mass and the road surface.

```text
Tire deflection = z1 - z0
```

The RMS value is calculated as:

```text
RMS_tire_deflection = rms(tire_deflection)
```

The passive suspension produced:

```text
RMS tire deflection = 	0.0064 m
```

### Passive Baseline

The final passive suspension performance is summarized below:

| Performance Metric | RMS Value |
|---|---:|
| Body acceleration | 1.5108 m/s² |
| Suspension travel | 0.0125 m |
| Tire deflection | 0.0064 m |

These values are treated as the **baseline performance** for evaluating the LQR-controlled active suspension.

The objective of the LQR controller is primarily to reduce body acceleration while maintaining suspension travel and tire deflection within acceptable ranges.
