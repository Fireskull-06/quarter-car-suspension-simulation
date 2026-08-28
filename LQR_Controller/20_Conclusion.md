## 20. Conclusion

A 2-DOF quarter-car suspension model was developed and implemented using MATLAB and Simulink. The model was first evaluated as a passive suspension 
system and then extended with an active suspension actuator controlled using an LQR state-feedback controller.

A systematic LQR parameter sweep was performed to study the trade-off between ride comfort, suspension behavior, and actuator effort. The final 
controller was selected based on a balance between reducing body acceleration and limiting control effort.

The final LQR controller produced the following results:

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

The closed-loop eigenvalues confirmed that the controlled system is stable, with all poles having negative real parts.

Overall, the simulation results demonstrate that the LQR-controlled active suspension can significantly reduce vehicle body acceleration while maintaining
similar suspension travel and only a small increase in tire deflection. The project demonstrates the complete workflow from physical suspension modeling 
and state-space formulation to controller design, simulation, parameter selection, stability analysis, and performance comparison.
