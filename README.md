# Quantum Computational Phase Transition in SAT problems
**Group 2607 Project**

This repository contains the implementation and analysis of the hybrid quantum-classical algorithm QAOA (Quantum Approximate Optimization Algorithm) applied to classic boolean satisfiability problems, with a specific focus on 2-SAT and preliminary results on 3-SAT problems. The project was structured within the LCP-B curriculum of the Master's degree in Physics of Data at the University of Padua.

## Project Objectives
The main goal is to investigate the effectiveness of quantum circuits in tackling SAT optimization problems, analyzing whether and how they provide an advantage over classical solvers. Particular attention is given to the simulation of the phase transition between the SAT and UNSAT regimes as a function of the critical density $\alpha = m/n$ (with characteristic densities $\alpha_c=1$ for 2-SAT and $\alpha_c=4.26$ for 3-SAT).

## Architecture and Implementation

### 1. Formula Generation and Classical Solutions
- **SAT Generator:** Object-oriented implementation using the `kSATGenerator` class to randomly sample and generate unique formulas and clauses, with integrated validation logic.
- **Brute-Force Solver:** Classical algorithm capable of exhaustively testing logical states ($2^n$) to identify valid boolean strings, also configurable for variants like 1-in-k-SAT.
- **Exact Max-SAT:** Module dedicated to the exploration of the entire computational spectrum in UNSAT regimes, aimed at the exact calculation of the maximum satisfiable clauses.

### 2. Quantum Ansatz and Optimization (QAOA)
- **Quantum Mapping:** Exact construction of the cost Hamiltonian $H_C$ and subsequent translation into operators within the Qiskit framework for circuit implementation.
- **Variational Circuits:** Definition of a parameterized quantum circuit of depth $p$ with evolution dictated by mixing and cost parameters $(\gamma_i, \beta_i)$.
- **Optimized Convergence:** Unlike traditional simulation based on finite sampling (shots), the computation relies on the exact analytical expectation value $\langle H_C \rangle$. This architecture eliminates statistical noise and significantly improves the convergence of classical optimizers, paving the way for complex operations such as parallel grid searches using Joblib.

The project has been developed using Qiskit and Joblib.
