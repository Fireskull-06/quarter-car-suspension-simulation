## 19. Discussion

The comparison between the passive and LQR-controlled suspension demonstrates the effect of active control on the quarter-car system.

The primary objective of the controller was to reduce body acceleration and improve ride comfort. The final LQR controller reduced RMS body acceleration from 1.3536 m/s² for the passive suspension to 0.5528 m/s², corresponding to an improvement of approximately 59.2%.

At the same time, RMS suspension travel decreased slightly from 0.0099 m to 0.0096 m. This indicates that the improvement in body acceleration was achieved without significantly increasing suspension movement.

RMS tire deflection increased slightly from 0.0065 m to 0.0067 m. This small increase represents a trade-off associated with the controller's emphasis on reducing body acceleration.

### Controller Trade-Off

The LQR parameter sweep showed that controller performance depends strongly on the relative weighting of system performance and actuator effort.

A very small value of `R` allows the controller to apply larger actuator forces and can produce very low body acceleration. However, this comes at the cost of increased actuator demand.

A larger value of `R` limits control effort but generally results in a higher body acceleration.

The final controller was therefore selected as a compromise rather than simply choosing the controller with the lowest possible body acceleration.

### Final Performance

The final configuration achieved:

```text
RMS body acceleration       = 0.5528 m/s²
RMS suspension travel       = 0.0096 m
RMS tire deflection         = 0.0067 m
```

Compared with the passive suspension:

```text
Body acceleration            → 59.2% reduction
Suspension travel            → 3.0% reduction
Tire deflection              → 3.1% increase
```

The closed-loop eigenvalues also confirmed that the final LQR controller produces a stable system, with all closed-loop poles having negative real parts.

Overall, the results show that LQR state-feedback control can substantially improve the ride-comfort response of the quarter-car suspension while maintaining comparable suspension travel and tire behavior.
