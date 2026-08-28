# Step 9 — Final Results and Conclusion

## Final Model

The completed project consists of a **2-DOF quarter-car suspension model** developed in MATLAB/Simulink.

The model represents the vertical dynamics of a representative SUV-class vehicle using:

- Sprung mass
- Unsprung mass
- Suspension spring
- Suspension damper
- Tire stiffness
- Road disturbance

The model was developed from the initial mathematical formulation through baseline simulation and suspension parameter optimization.

---

## Final Parameters

The final optimized model uses the following parameters:

| Parameter | Symbol | Final Value | Unit |
|---|---:|---:|---|
| Unsprung mass | $m_1$ | 40 | kg |
| Sprung mass | $m_2$ | 400 | kg |
| Suspension stiffness | $K_s$ | **15,000** | N/m |
| Suspension damping | $C_s$ | **600** | Ns/m |
| Tire stiffness | $K_t$ | 190,000 | N/m |

The vehicle masses and tire stiffness were kept constant, while the suspension stiffness and damping were optimized.

---

## Baseline vs Optimized Parameters

| Parameter | Baseline | Optimized |
|---|---:|---:|
| Suspension stiffness, $K_s$ | 20,000 N/m | **15,000 N/m** |
| Suspension damping, $C_s$ | 1,500 Ns/m | **600 Ns/m** |

The optimization resulted in a reduction of both suspension stiffness and damping relative to the baseline configuration.

---

## Performance Metrics

The suspension was evaluated using three primary performance metrics:

### RMS Body Acceleration

Used as an indicator of the vibration transmitted to the vehicle body and therefore ride comfort.

### RMS Suspension Travel

Used to evaluate the relative movement between the sprung and unsprung masses.

$$
x_{travel} = x_2-x_1
$$

### RMS Tire Deflection

Used to evaluate the relative movement between the unsprung mass and the road.

$$
x_{tire} = x_1-x_r
$$

---

## Final Results

The final comparison between the baseline and optimized configurations is shown below.

| Performance Metric | Baseline | Optimized | Percent Change |
|---|---:|---:|---:|
| RMS Body Acceleration | **1.3609** | **0.8338** | **38.7317** |
| RMS Suspension Travel | **0.0104** | **0.0122** | **17.3077** |
| RMS Tire Deflection | **0.006** | **0.007** | **16.6667** |

The exact improvement values are calculated from the simulation outputs.
We minimized acceleration which increased our comfort at the cost of increased suspension and tire deflection.
---

## Overall Outcome

The project demonstrated the complete workflow for developing and optimizing a 2-DOF quarter-car suspension system:

```text
Parameter Establishment
        ↓
Mathematical Model
        ↓
Simulink Implementation
        ↓
Road Profile Development
        ↓
Baseline Simulation
        ↓
Performance Evaluation
        ↓
Parameter Optimization
        ↓
Baseline vs Optimized Comparison
