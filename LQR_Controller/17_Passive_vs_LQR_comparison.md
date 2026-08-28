## 17. Passive vs LQR Performance Comparison

The final LQR-controlled suspension is compared with the passive suspension using the same quarter-car parameters and the same 50 mm road bump.

This ensures that the comparison is performed under identical conditions and that the observed differences are due to the LQR controller.

### Performance Comparison

| Performance Metric | Passive | LQR | Improvement |
|---|---:|---:|---:|
| RMS body acceleration | 1.3536 m/s² | 0.5528 m/s² | 59.2% reduction |
| RMS suspension travel | 0.0099 m | 0.0096 m | 3.0% reduction |
| RMS tire deflection | 0.0065 m | 0.0067 m | 3.1% increase |

### Body Acceleration

The most significant improvement is observed in RMS body acceleration.

The passive suspension produces:

```text
1.3536 m/s²
```

while the LQR-controlled suspension produces:

```text
0.5528 m/s²
```

The percentage reduction is calculated as:

```text
Improvement = ((Passive - LQR) / Passive) * 100
```

Therefore:

```text
Improvement = ((1.3536 - 0.5528) / 1.3536) * 100
            = 59.2%
```

The LQR controller therefore reduces RMS body acceleration by approximately **59.2%**, indicating a substantial improvement in ride comfort.

### Suspension Travel

The RMS suspension travel changes from:

```text
Passive = 0.0099 m
LQR     = 0.0096 m
```

This corresponds to approximately a **3.0% reduction** in suspension travel.

This indicates that the controller improves body acceleration without requiring greater overall suspension travel.

### Tire Deflection

The RMS tire deflection changes from:

```text
Passive = 0.0065 m
LQR     = 0.0067 m
```

This represents an increase of approximately **3.1%**.

Although tire deflection increases slightly, the change is small compared with the significant reduction in body acceleration.

### Overall Result

The comparison demonstrates that the LQR controller provides a substantial improvement in the primary ride-comfort metric while maintaining similar suspension travel and only slightly increasing tire deflection.

The final results can therefore be summarized as:

```text
Body acceleration       → 59.2% reduction
Suspension travel       → 3.0% reduction
Tire deflection         → 3.1% increase
```

The response plots generated from the Simulink simulations provide a visual comparison of the passive and active suspension behavior and are included in the following section.
