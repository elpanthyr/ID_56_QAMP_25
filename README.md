# QAMP Project #56: Reinforcement Learning Based Selection of Error Mitigation Parameters for Zero Noise Extrapolation

## Project Overview
This project implements a Reinforcement Learning (RL) framework to optimize Zero-Noise Extrapolation (ZNE), a quantum error mitigation technique. Standard ZNE often relies on fixed noise-scaling parameters (e.g., linear extrapolation with specific scale factors), which may not be optimal for circuits of varying depths and noise profiles.

Our approach utilizes a Double Deep Q-Network (DDQN) agent to dynamically select the most effective noise scaling factors and extrapolation methods (Linear, Polynomial, or Richardson) based on the topological features of the input quantum circuit.

## Methodology
The framework treats error mitigation as a control problem where an RL agent interacts with a noisy quantum simulation environment.

* **Input:** Variable-depth quantum circuits (EfficientSU2 ansatz).
* **State Space:** Topological features of the circuit, including depth, 2-qubit gate count, total gate density, and parameter count.
* **Action Space:** A discrete set of noise-scaling templates (e.g., `[1, 2, 3]`, `[1, 3, 5]`) paired with specific extrapolators. The agent also has access to an "Identity" action to bypass mitigation for shallow circuits where overhead outweighs benefit.
* **Reward Function:** Defined by the relative reduction in error compared to the unmitigated hardware execution.

## Performance Results
The reinforcement learning agent demonstrated significant performance gains over standard fixed-template baselines.

* **Relative Improvement:** Achieved a **54.21% relative improvement** in error reduction compared to standard Richardson extrapolation.
* **Error Reduction:** Reduced the mean error from **0.0816** (Standard Baseline) to **0.0374** (RL Agent) on the test set.
* **Adaptive Strategy:** The agent successfully learned a depth-dependent policy, applying aggressive mitigation for deep circuits while preserving fidelity on shallow circuits by defaulting to identity operations.

## Repository Contents
This repository contains the Jupyter Notebooks used for training and evaluating the RL agent.

1.  **Training Notebook(s):** Contains the environment setup, DDQN agent architecture, and the training loop with curriculum learning.
2.  **Testing & Visualization Notebook(s):** Loads the trained model to evaluate performance against baselines and generates performance metrics/plots.

## Usage
To replicate the results:
Download and run in google colab

## Team
**Mentors:**
* Dr. Ritajit Majumdar
* Dr. Anupama Ray

**Mentees:**
* Deenathayalan A(https://github.com/elpanthyr)
* Abdullah K(https:github.com/AbdullahKazi500)

## Acknowledgements
This work was conducted as part of the Qiskit Advocates Mentorship Program (QAMP) 2025.
