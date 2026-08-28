## 15. Closed-Loop Stability Analysis

After obtaining the final LQR gain, the stability of the controlled quarter-car system was verified by calculating the eigenvalues of the closed-loop system.

The closed-loop state matrix is defined as:

```text
A_cl = A - B*K_final
```

The eigenvalues were calculated in MATLAB using:

```matlab
eig(A-B*K_final)
```

The resulting closed-loop eigenvalues were:

```text
-7.0921 + 68.9369i
-7.0921 - 68.9369i
-2.4348 + 3.5268i
-2.4348 - 3.5268i
```

### Stability Result

All four eigenvalues have negative real parts:

```text
Real(λ) < 0
```

Therefore, the closed-loop system is asymptotically stable.

The two pairs of complex-conjugate poles represent the oscillatory modes of the controlled quarter-car system. The negative real components indicate that these oscillations decay with time rather than growing.

### MATLAB Verification

The stability condition was verified using:

```matlab
eig(A-B*K_final)
```

Since all closed-loop poles lie in the left half of the complex plane, the final LQR controller provides a stable closed-loop suspension system.

The stable controller was then implemented in Simulink for the final active suspension simulation.
