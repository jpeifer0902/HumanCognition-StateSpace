# HumanCognition-StateSpace
A systems-level model of cognitive stability and learning efficiency under constraint.

## Overview
Human cognitive performance is often discussed in qualitative or static terms. This project models cognition as a resource-limited, dynamic system that evolves over time under constraint.

## Core Idea
Cognitive capacity, learning efficiency, and executive function interact nonlinearly with factors such as:
- Sleep debt
- Cognitive load
- Stress
- Recovery inputs
Small, cumulative constraints can push the system toward instability.

## Framework
This model is inspired by:
- HSI
- Cognitive Neuroscience
- State-space and control systems intuition
Key features:
- Explicit assumptions
- Noise and variability
- Degradation and recovery dynamics

## Why This Matters
Understanding cognition as a dynamic system has implications for:
- Learning design
- Neurodivergent support
- Human-in-the-loop engineering
- Sustainable performance under constraint

## Status
Initial conceptual model and prototype simulation.

## Model Assumptions and Equations
This model treats human cognition as a resource-limited dynamical system evolving over discrete time.

### State Variables
- Sleep debt S(t)
- Cognitive capacity C(t)
- Learning efficiency L(t)

### Core Assumptions
- Cognitive capacity degrades as cumulative sleep debt increases.
- Recovery exhibits diminishing returns as sleep debt grows.
- Learning efficiency is bounded and proportional to available cognitive capacity.
- Human performance is inherently noisy and variable.

### Update Equations (Conceptual)

Sleep debt accumulation:
S(t+1) = S(t) + α

Cognitive capacity update:
C(t+1) = C(t) - β ⋅ S(t) + γ ⋅ e ^ (—S(t)) + ε

Learning efficiency:
L(t) = clamp(C(t), 0, 1)

where α represents daily sleep loss, β represents cognitive degradation sensitivity, γ represents recovery strength, and ε represents stochastic noise.

### Limitations

This model is intentionally simplified and is not intended to capture the full biological or psychological complexity of human cognition.
- The state variables represent abstracted constructs rather than directly measurable neurobiological quantities.
- Parameter values (α, β, γ, ε) are illustrative and not empirically fitted to individual-level data.
- The model assumes time-invariant dynamics over time, ignoring circadian effects, task heterogeneity, and inter-individual variability.
- Recovery dynamics are modeled as a smooth nonlinear function and do not explicitly represent sleep archetecture, neurochemical processes, or long-term adaptation.
- Stochastic noise is modeled as Guassian and independent across time steps, which might not reflect structured or autocorrelated sources of variability in real-world cognition.

Despite these limitations, the framework is useful for conceptual exploration, hypothesis generation, and reasoning about trade-offs in learning, fatigue, and recovery under restraint.


# Plot results
```python
time = np.arange(T)

plt.figure(figsize = (8, 5))
plt.plot(time, cognitive_capacity, label = "Cognitive Capacity C(t)")
plt.plot(time, learning_efficiency, label = "Learning Efficiency L(t)", linestyle = "--")

plt.xlabel("Time (days)")
plt.ylabel("Normalized Value")
plt.title("Cognitive Capacity and Learning Efficiency Under Sleep Debt")
plt.legend()
plt.tight_layout()
plt.show()
```
## How to Run

This model can be run locally to simulate cognitive capacity and learning efficiency over time.

### Requirements
- Python
- NumPy
- Matplotlib

### Run
```bash
python cognitive_model.py
```

## Future Work

Potential extensions of this framework include:

- Incorporating circadian dynamics and sleep architecture (e.g., REM/NREM cycles).
- Allowing parameter values to vary across individuals or tasks.
- Modeling recovery as a function of active rest, task switching, or strategic breaks.
- Introducing memory consolidation or long-term learning effects.
- Calibrating parameters using empirical cognitive or behavioral data.
