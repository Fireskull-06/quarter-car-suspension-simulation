# Establishing Vehicle Parameters

## 2-DOF Quarter-Car Suspension Model

**Vehicle:** 

The first step in developing the 2-DOF quarter-car suspension model was to establish the vehicle and suspension parameters required for the simulation.

These parameters define the **baseline suspension configuration** and serve as the reference for the subsequent suspension optimization process.

---

## Vehicle Parameters

### Unsprung Mass

The unsprung mass represents the wheel, tire, and other components associated with the wheel assembly.

**m₁ = 40 kg**

### Sprung Mass

The sprung mass represents the portion of the vehicle body supported by the suspension in the quarter-car model.

**m₂ = 400 kg**

---

## Baseline Suspension Parameters

The following values represent the original suspension configuration used for the baseline simulation.

### Suspension Stiffness

The suspension stiffness represents the stiffness of the suspension spring.

**Kₛ = 20,000 N/m**

### Suspension Damping

The suspension damping coefficient represents the damping provided by the suspension damper.

**Cₛ = 1,500 Ns/m**

---

## Tire Parameter

### Tire Stiffness

The tire stiffness represents the vertical stiffness of the tire and determines how the tire responds to the road input.

**Kₜ = 190,000 N/m**

---

## Parameter Summary

| Parameter            | Symbol |   Value | Unit |
| -------------------- | -----: | ------: | ---- |
| Unsprung mass        |     m₁ |      40 | kg   |
| Sprung mass          |     m₂ |     400 | kg   |
| Suspension stiffness |     Kₛ |  20,000 | N/m  |
| Suspension damping   |     Cₛ |   1,500 | Ns/m |
| Tire stiffness       |     Kₜ | 190,000 | N/m  |

---

## Baseline Configuration

The established baseline parameters are:

* **m₁ = 40 kg**
* **m₂ = 400 kg**
* **Kₛ = 20,000 N/m**
* **Cₛ = 1,500 Ns/m**
* **Kₜ = 190,000 N/m**

These values form the initial configuration of the representative car

The suspension stiffness and damping values are later varied during the optimization stage to determine an improved suspension configuration while keeping the vehicle masses \
and tire stiffness constant.
