# Step 8 — Baseline vs Optimized Performance Comparison

## Overview

After obtaining the optimized suspension parameters, the final step was to compare the optimized configuration with the original baseline configuration.

The purpose of this comparison was to determine whether changing the suspension stiffness and damping resulted in an improvement in the overall suspension performance.

Both configurations were evaluated using the same:

- 2-DOF quarter-car model
- Vehicle mass parameters
- Tire stiffness
- Road profile
- Simulation conditions
- Performance metrics

This ensured that the comparison was performed under identical conditions.

---

## Baseline Configuration

The original suspension configuration was:

$$
K_s = 20,000\;N/m
$$

$$
C_s = 1,500\;Ns/m
$$

The remaining parameters were:

$$
m_1 = 40\;kg
$$

$$
m_2 = 400\;kg
$$

$$
K_t = 190,000\;N/m
$$

---

## Optimized Configuration

The optimized suspension configuration obtained in Step 7 was:

$$
K_s = 15,000\;N/m
$$

$$
C_s = 600\;Ns/m
$$

The vehicle masses and tire stiffness remained unchanged.

---

## Parameter Comparison

| Parameter | Baseline | Optimized | Change |
|---|---:|---:|---:|
| Unsprung mass, $m_1$ | 40 kg | 40 kg | No change |
| Sprung mass, $m_2$ | 400 kg | 400 kg | No change |
| Suspension stiffness, $K_s$ | 20,000 N/m | 15,000 N/m | Reduced |
| Suspension damping, $C_s$ | 1,500 Ns/m | 600 Ns/m | Reduced |
| Tire stiffness, $K_t$ | 190,000 N/m | 190,000 N/m | No change |

The optimization therefore modified only the suspension stiffness and damping.

---

## Performance Comparison

The baseline and optimized configurations were evaluated using three RMS performance metrics:

1. RMS Body Acceleration
2. RMS Suspension Travel
3. RMS Tire Deflection

The results are summarized below.

| Performance Metric | Baseline | Optimized | Change |
|---|---:|---:|---:|
| RMS Body Acceleration | **[Insert value]** | **[Insert value]** | **[Insert %]** |
| RMS Suspension Travel | **[Insert value]** | **[Insert value]** | **[Insert %]** |
| RMS Tire Deflection | **[Insert value]** | **[Insert value]** | **[Insert %]** |

---

## Percentage Change

The percentage change for each performance metric can be calculated using:

$$
\%\;Change =
\frac{Baseline-Optimized}{Baseline}
\times100
$$

For metrics where a lower value represents better performance, a positive percentage indicates an improvement.

---

## Response Comparison

The simulation responses of the baseline and optimized configurations were compared using the same road disturbance.

The primary bump in the road profile occurs at approximately:

$$
t \approx 1.36\;s
$$

The comparison allows the effect of the optimized suspension parameters to be observed directly in the transient response.

### Baseline Response

![Baseline Response](images/baseline_output.png)

### Optimized Response

![Optimized Response](images/optimized_output.png)

---

## Results Interpretation

The comparison between the two configurations provides an objective assessment of the optimization.

The optimized suspension parameters:

$$
K_s = 15,000\;N/m
$$

$$
C_s = 600\;Ns/m
$$

were selected based on their overall performance across the defined suspension metrics.

The final assessment considers the trade-off between ride comfort, suspension travel, and tire deflection rather than evaluating only one performance measure.

---

## Final Configuration

The final optimized 2-DOF quarter-car model uses:

| Parameter | Final Value | Unit |
|---|---:|---|
| Unsprung mass, $m_1$ | 40 | kg |
| Sprung mass, $m_2$ | 400 | kg |
| Suspension stiffness, $K_s$ | **15,000** | N/m |
| Suspension damping, $C_s$ | **600** | Ns/m |
| Tire stiffness, $K_t$ | 190,000 | N/m |

---

## Conclusion

The baseline and optimized suspension configurations were simulated under identical road and model conditions.

The optimization reduced the suspension stiffness from **20,000 N/m to 15,000 N/m** and the suspension damping from **1,500 Ns/m to 600 Ns/m**.

The resulting performance metrics provide a quantitative basis for determining the effectiveness of the optimized suspension configuration.

This completes the development, simulation, and optimization of the **2-DOF quarter-car suspension model**.
