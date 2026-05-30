# Simulated Annealing for the Travelling Salesman Problem (TSP)

This repository contains the Python implementation of the **Simulated Annealing (SA)** algorithm applied to the **Travelling Salesman Problem (TSP)**. The project explores the isomorphism between combinatorial optimization and Statistical Mechanics, treating the cost function as a Hamiltonian and analyzing the system's phase transitions through its specific heat.

To break the thermodynamic limits and approach the absolute theoretical bound (Beardwood's limit $\approx 0.749$), the algorithm is progressively improved through three distinct methodological phases.

## Project Structure

The project is divided into three Jupyter Notebooks, each representing a step forward in optimization and heuristic complexity:

### 1. Base Model (`TSP.ipynb`)
* **Description:** Standard implementation of the Simulated Annealing algorithm using the classic Metropolis criterion. It proposes global, random 2-OPT topological transitions across a map of 400 cities.
* **Characteristics:** Preserves strict thermodynamic equilibrium and detailed balance. It perfectly matches the theoretical predictions (Bonomi and Lutton's continuous model) but suffers from stochastic trapping at low temperatures, resulting in a final cost error of ~9.7%.

### 2. Spatial Restriction (`TSP_vecinos.ipynb`)
* **Description:** An optimization introducing a geographical bias. The 2-OPT transitions are restricted exclusively to the $m=15$ nearest neighbors of the selected node.
* **Characteristics:** Prevents the algorithm from proposing unviable macroscopic connections at extremely low temperatures. It breaks the previous local minimum, reduces the asymptotic error to ~4.7%, and maintains acceptable thermodynamic validity, delaying the structural freezing of the system.

### 3. Stochastic Beam Search (`TSP_vecinos_beamsearch.ipynb`)
* **Description:** A hybrid algorithm combining the spatial restriction with a probabilistic Beam Search. It simultaneously evaluates a beam of $B=8$ local candidate branches and selects the transition using a local Boltzmann probability distribution.
* **Characteristics:** Achieves maximum combinatorial performance, reaching a final cost error of just **0.69%**. This intense selection pressure intentionally breaks the canonical thermodynamic equilibrium (causing a "quenching" effect), sacrificing theoretical statistical physics for supreme topological optimization.

## Requirements

To run the notebooks, you will need the following Python libraries:
* `numpy` (for matrix operations and mathematical modeling)
* `matplotlib` (for plotting the energy landscapes, specific heat, and routing maps)
* `tqdm` (for tracking the Monte Carlo simulation progress)
