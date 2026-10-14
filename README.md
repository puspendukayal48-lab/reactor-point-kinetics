# Reactor Point Kinetics Simulation

A simplified point-kinetics model of nuclear reactor power response, 
built to understand reactivity, delayed neutrons, and prompt criticality.

## What it does
Solves the point-kinetics equations (one-group delayed neutron approximation)
using scipy's solve_ivp, showing reactor power (n) and precursor concentration (C)
over time under different reactivity (ρ) insertions.

## Key results
- Subcritical/mild reactivity (ρ < β): fast initial jump, then slow controllable climb
- Prompt supercritical (ρ > β): near-instant exponential runaway, 
  demonstrating why this threshold must never be crossed in practice
  
## Update: Six-Group Delayed Neutron Model

Why the One-Group Model Was a Simplification

The one-group delayed neutron model treats all delayed neutron precursors as a single effective group with one average decay constant. In reality, delayed neutrons are emitted by several different groups of radioactive fission products, each with its own characteristic decay constant and half-life. Consequently, different precursor groups release delayed neutrons at different rates. The six-group model represents this diversity more realistically by tracking six separate precursor groups.

What Changed in the Model

The model was extended from two coupled differential equations to seven coupled equations: one equation describing the neutron population and six equations describing the individual delayed neutron precursor groups. Each precursor group has its own delayed neutron fraction, beta_i, and decay constant, lambda_i. This allows the model to account for the distinct decay behaviour of each group rather than approximating all delayed neutron emission with a single average.

Results and Comparison

At the same reactivity, rho = 0.001, the six-group model reached a higher power level by t = 20s than the one-group model. One possible explanation is that the six-group model captures the different timescales of delayed neutron emission more accurately. Shorter-lived precursor groups can release delayed neutrons relatively quickly, whereas longer-lived groups contribute over extended periods. A single effective decay constant cannot represent all these timescales simultaneously, so the one-group model may predict a different transient response.

However, the higher power observed in the six-group model is specific to the parameters and initial conditions used in this simulation; it is not a universal consequence of using six groups. The result should therefore be interpreted by examining the selected group constants and the resulting neutron population over time.

Prompt-Supercritical Case

For the prompt-supercritical case, rho = 0.007, the model continued to exhibit rapid, approximately exponential power growth, consistent with the behaviour observed in the earlier simulation. This indicates that the extended model retains the expected qualitative behaviour in this regime. A quantitative validation would require checking the numerical solution against the model equations and confirming that the time integration remains accurate during the rapid transient.

## Background
Built while self-studying nuclear engineering fundamentals alongside GATE EE prep,
working toward M.Tech in Nuclear Engineering.
