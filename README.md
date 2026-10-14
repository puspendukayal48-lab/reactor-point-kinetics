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

## Background
Built while self-studying nuclear engineering fundamentals alongside GATE EE prep,
working toward M.Tech in Nuclear Engineering.
