# Time Reversibility and Chaos: Hard Sphere Billiard Simulation

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

This Numerical Simulation project (ESPCI Paris - 2nd Year) explores the limits of time reversibility in a chaotic Hamiltonian system: a 2D gas of hard spheres.

By comparing standard floating-point arithmetic (IEEE 754) with **arbitrary precision arithmetic**, we analyze the **Loschmidt Echo** phenomenon and how round-off errors drive the exponential divergence of trajectories.

## 🎯 Objectives

* **Simulate** a particle system (billiards) using an **Event-Driven Molecular Dynamics** approach.
* **Test** time reversibility by instantaneously inverting velocities ($t \to -t$) at $t_{simul}/2$.
* **Quantify** chaos and sensitivity to initial conditions.
* **Improve** numerical accuracy using the `mpmath` library to delay the onset of chaotic divergence.

## ⚙️ Key Features

* **Event-Driven Physics Engine:** Predicts exact collision times (particle-particle and particle-wall) without fixed time steps, solving quadratic equations for contact conditions.
* **Arbitrary Precision:** Integration of `mpmath` to define custom decimal precision (e.g., `mp.dps = 50`), overcoming 64-bit float limitations.
* **Crystalline Initialization:** 15-particle triangular lattice target impacted by a projectile, with controlled stochastic perturbation ($\epsilon$) to avoid numerical singularities.
* **Error Metrics:** Calculation of position reconstruction error ($\mathcal{L}_{pos}$) and velocity error ($\mathcal{L}_{vel}$).

## 📂 Project Structure

* `Simul.py`: Core class handling physics, collision detection (`wall_time`, `pair_time`), and state updates (`md_step`).
* `Animate.py`: Handles graphical rendering and high-precision data conversion for visualization.
* `main.py`: Simulation orchestration, time loops, and velocity inversion logic.

## 🚀 Installation & Usage

### Prerequisites
The project requires Python and the following libraries:
```bash
pip install numpy matplotlib mpmath
