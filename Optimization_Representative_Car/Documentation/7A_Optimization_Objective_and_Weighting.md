# Step 7A — Optimization Objective and Weighting

## Overview

The suspension optimization was formulated as a multi-objective problem using three RMS performance metrics obtained from the 2-DOF quarter-car simulation:

- RMS Body Acceleration
- RMS Suspension Travel
- RMS Tire Deflection

Since these metrics represent different aspects of suspension performance, weighted objective functions were used to evaluate different design priorities.

---

## Normalization

Before applying the weights, each RMS performance metric was normalized.

The normalized metrics were:

- **aₙ** = normalized RMS body acceleration
- **xₙ** = normalized RMS suspension travel
- **dₙ** = normalized RMS tire deflection

Normalization allowed the three performance metrics to be combined into a common dimensionless objective function.

For the final optimized configuration, the normalized values were:

| Performance Metric | RMS Value | Normalized Value |
|---|---:|---:|
| Body acceleration | 0.62560 m/s² | 0.46568 |
| Suspension travel | 0.011611 m | 0.82617 |
| Tire deflection | 0.0063468 m | 0.88246 |

---

## Objective Functions

Three different weighting approaches were evaluated:

1. Comfort-oriented optimization
2. Balanced optimization
3. Handling-oriented optimization

This allowed the effect of different performance priorities to be investigated.

---

# 1. Comfort-Oriented Objective

The comfort-oriented objective assigned the greatest importance to RMS body acceleration.

### Comfort Weights

| Performance Metric | Weight |
|---|---:|
| RMS Body Acceleration | 0.60 |
| RMS Suspension Travel | 0.25 |
| RMS Tire Deflection | 0.15 |

### Objective Function

**J₍comfort₎ = 0.60aₙ + 0.25xₙ + 0.15dₙ**

For the final optimized configuration:

**J₍comfort₎ = 0.60(0.46568) + 0.25(0.82617) + 0.15(0.88246)**

**J₍comfort₎ = 0.61832**

This objective places the greatest emphasis on ride comfort.

---

# 2. Balanced Objective

The balanced objective gave greater consideration to suspension travel and tire deflection while still maintaining body acceleration as the most important individual metric.

### Balanced Weights

| Performance Metric | Weight |
|---|---:|
| RMS Body Acceleration | 0.50 |
| RMS Suspension Travel | 0.30 |
| RMS Tire Deflection | 0.20 |

### Objective Function

**J₍balanced₎ = 0.50aₙ + 0.30xₙ + 0.20dₙ**

For the final optimized configuration:

**J₍balanced₎ = 0.50(0.46568) + 0.30(0.82617) + 0.20(0.88246)**

**J₍balanced₎ = 0.65718**

The same value was reported by MATLAB as:

**Score_Weighted = 0.65718**

Therefore, the weighted objective used for the final parameter selection corresponds to the balanced weighting shown above.

---

# 3. Handling-Oriented Objective

A separate handling-oriented objective was also evaluated.

The handling optimization produced the following configuration:

| Parameter | Value |
|---|---:|
| Suspension stiffness, Kₛ | 15,000 N/m |
| Suspension damping, Cₛ | 600 Ns/m |

The corresponding handling score was:

**Score_Handling = 0.69605**

The handling-oriented objective was included to evaluate the suspension from a different performance-priority perspective.

The exact individual handling weights are not documented here because they were not independently recovered from the available MATLAB output.

---

## Comparison of Objective Scores

For the final optimized configuration:

| Objective | Score |
|---|---:|
| Comfort | **0.61832** |
| Balanced / Weighted | **0.65718** |
| Handling | **0.69605** |

The three objectives therefore provide different numerical evaluations of the same suspension configuration.

---

## Optimization Result Consistency

An important observation from the optimization results is that the same suspension parameters were obtained for the evaluated optimization approaches:

**Kₛ = 15,000 N/m**

**Cₛ = 600 Ns/m**

The corresponding simulation results were:

| Metric | Value |
|---|---:|
| RMS Body Acceleration | 0.62560 m/s² |
| RMS Suspension Travel | 0.011611 m |
| RMS Tire Deflection | 0.0063468 m |

This consistency provides additional confidence in the selected suspension parameter combination.

---

## Why Multiple Weightings Were Used

Suspension design involves competing objectives.

Reducing body acceleration can improve ride comfort, but changes in suspension stiffness and damping can also affect suspension travel and tire behavior.

Using multiple weighting schemes allows the design to be evaluated from different perspectives rather than relying on a single performance criterion.

The three approaches used in the analysis were intended to represent:

### Comfort

Prioritizes reduction of body vibration.

### Balanced

Provides a compromise between body acceleration, suspension travel, and tire deflection.

### Handling

Provides an additional evaluation of suspension behavior using a handling-oriented objective.

---

## Final Weighted Objective

For the final parameter selection, the balanced weighting was used:

**J = 0.50aₙ + 0.30xₙ + 0.20dₙ**

where:

- **aₙ** = normalized RMS body acceleration
- **xₙ** = normalized RMS suspension travel
- **dₙ** = normalized RMS tire deflection

The resulting optimized parameters were:

**Kₛ = 15,000 N/m**

**Cₛ = 600 Ns/m**

---

## Key Takeaways

- The RMS performance metrics were normalized before being combined.
- Multiple weighting schemes were evaluated.
- The comfort objective used weights of **0.60, 0.25, and 0.15**.
- The balanced/weighted objective used weights of **0.50, 0.30, and 0.20**.
- The balanced/weighted objective produced a score of **0.65718** for the final configuration.
- The same optimized suspension parameters were obtained across the evaluated optimization approaches.
- The final optimized suspension configuration was:

**Kₛ = 15,000 N/m**

**Cₛ = 600 Ns/m**
