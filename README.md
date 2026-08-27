# Quarter-Car Suspension Modeling & Control

Progressive development of a quarter-car suspension model in MATLAB/Simulink — from a baseline 1-DOF representation to a fully optimized 2-DOF system with active control.

## Project Progression

This project was built in four stages, each one extending the previous:

1. **1-DOF Model** — baseline sprung-mass dynamics
2. **2-DOF Model** — coupled sprung/unsprung mass dynamics
3. **Passive Parameter Optimization** — grid search over suspension stiffness and damping
4. **Active Control** — LQR-based active suspension layered on the optimized model

---

## 1. 1-DOF Model

Started with a simplified single-degree-of-freedom model representing only the sprung mass (vehicle body) connected to the road through a single spring-damper element. This established a baseline understanding of body-response behavior and validated the overall modeling approach before adding the complexity of unsprung mass dynamics.

## 2. 2-DOF Quarter-Car Model

Extended the model to a standard quarter-car representation with coupled sprung and unsprung masses, capturing both body dynamics and wheel/tire behavior under road excitation. This model forms the basis for all the optimization and control work that follows, and RMS body acceleration, suspension travel, and tire deflection were tracked as the key performance metrics throughout.

## 3. Passive Parameter Optimization

Ran a grid search over suspension stiffness and damping values, evaluated against comfort-focused, handling-focused, and balanced objectives. The comfort-optimized configuration achieved a significant reduction in RMS body acceleration compared to the passive baseline, at a controlled trade-off in suspension travel and tire deflection — showing that a deliberate design choice, not just a blanket improvement, was made based on the priorities of the objective.

## 4. Active Suspension Control (LQR)

Building on the optimized passive model, added an active suspension controller using a Linear Quadratic Regulator (LQR) to further improve ride comfort beyond what passive tuning alone could achieve. This stage benchmarks performance across three configurations — passive baseline, optimized passive, and active control — to show the full progression of the suspension design and quantify how much additional benefit active control provides over passive optimization alone.

---

## Tech Stack

- MATLAB / Simulink
- Control System Toolbox

## Future Work

- Validate against a random road-roughness input in addition to the standardized bump excitation
- Compare LQR against a semi-active skyhook controller
- Incorporate frequency-weighted comfort standards into the objective function

---

*Detailed results, tables, and plots to be added.*
