## 4. Mathematical Model

The quarter-car system is modeled using two degrees of freedom: the vertical motion of the sprung mass and the vertical motion of the unsprung mass.

The variables used are:

- z2 = sprung-mass displacement
- z1 = unsprung-mass displacement
- z0 = road displacement
- u = active suspension actuator force

### Sprung Mass Equation

The sprung mass is affected by the suspension spring, suspension damper, and actuator force.

```text
m2*z2_ddot = -Ks*(z2 - z1) - Cs*(z2_dot - z1_dot) + u
