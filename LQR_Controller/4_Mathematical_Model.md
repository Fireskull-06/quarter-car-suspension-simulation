## 4. Mathematical Model

The quarter-car system is modeled using two degrees of freedom: the vertical motion of the sprung mass and the vertical motion of the unsprung mass.

Let:

- \(z_2\) = sprung-mass displacement
- \(z_1\) = unsprung-mass displacement
- \(z_0\) = road displacement
- \(u\) = active suspension actuator force

The equations of motion are derived using Newton's second law.

### Sprung Mass

The forces acting on the sprung mass are the suspension spring force, suspension damping force, and active actuator force.

\[
m_2\ddot{z}_2 =
-K_s(z_2-z_1)
-C_s(\dot{z}_2-\dot{z}_1)
+u
\]

Therefore,

\[
m_2\ddot{z}_2 =
-K_s(z_2-z_1)
-C_s(\dot{z}_2-\dot{z}_1)
+u
\]

### Unsprung Mass

The unsprung mass is affected by the suspension forces, tire force, and the actuator reaction force.

\[
m_1\ddot{z}_1 =
K_s(z_2-z_1)
+C_s(\dot{z}_2-\dot{z}_1)
-K_t(z_1-z_0)
-u
\]

where \(z_0\) represents the vertical displacement of the road surface.

### Passive Suspension

For the passive suspension case, there is no active actuator force:

\[
u=0
\]

The same physical model is therefore used for the baseline simulation, with only the active control force removed.

### Active Suspension

For the active suspension case, the actuator force is generated using state feedback:

\[
u=-Kx
\]

where \(K\) is the LQR feedback gain matrix and \(x\) is the system state vector.
