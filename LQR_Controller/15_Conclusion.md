## 15. Conclusion

A 2-DOF quarter-car suspension model was developed and implemented using MATLAB and Simulink. The model was first evaluated as a passive suspension 
system and then extended with an active suspension actuator controlled using an LQR state-feedback controller.

A systematic LQR parameter sweep was performed to study the trade-off between ride comfort, suspension behavior, and actuator effort. The final 
controller was selected based on a balance between reducing body acceleration and limiting control effort.

The final LQR controller produced the following results:

```text
RMS body acceleration       = 0.7009 m/s²
RMS suspension travel       = 0.0125 m
RMS tire deflection         = 0.0077 m
```

Compared with the passive suspension:

```text
Body acceleration            → 53.60% improvement
Suspension travel            → 0.41% worse (essentially unchanged)
Tire deflection              → 20.57% worse
```

The closed-loop eigenvalues confirmed that the controlled system is stable, with all poles having negative real parts.

Overall, the simulation results demonstrate that the LQR-controlled active suspension can significantly reduce vehicle body acceleration while maintaining
similar suspension travel and only an increase in tire deflection. The project demonstrates the complete workflow from physical suspension modeling 
and state-space formulation to controller design, simulation, parameter selection, stability analysis, and performance comparison.
