# Emergency Patient Transportation — Quantum Vehicle Routing Problem (VRP)

The Vehicle Routing Problem (VRP) represents one of the world’s largest operational challenges, with its global market estimated at approximately USD 8.2 trillion (2015).

Typical VRP scenarios involve a fleet of vehicles (such as trucks, ambulances, or container ships), depots where these vehicles are stationed, and multiple client locations that must be served within given constraints.

The central computational challenge is to design efficient routes that start and end at depots while visiting a set of locations, with the goal of minimizing total travel distance, travel time, or other performance metrics.

# Problem Context

In this work, we consider a specialized instance of the VRP that is highly relevant to modern smart-city infrastructure: Emergency Patient Transportation in the New Capital City.

In this scenario, traffic optimization plays a critical role in sustainability, fuel efficiency, and public well-being.
We study the case of urgent patient transfers where a single ambulance must transport five patients to a central hospital.

# Problem Statement

We consider the case of a single ambulance that must transport five patients to a central hospital under emergency conditions.
The ambulance is allowed to perform multiple trips, but each trip can accommodate at most three patients due to capacity constraints.

All patients must be delivered safely to the hospital, and travel distances are computed using real GPS coordinates for both the hospital and the patient locations.

# Objective

Determine an optimal routing strategy that minimizes the total travel distance required to serve all patients, while respecting the capacity and feasibility constraints of the problem.

# Dataset

The instance data (hospital and patient coordinates, pairwise distances) are provided in the JSON file:
OptimizationProblemData.json
Distance calculations are based on GPS coordinates.

# Proposed Methodology
## Overview of the Pipeline

The proposed pipeline provides an end-to-end framework for addressing the ambulance routing problem.
The methodology is structured in two complementary phases:

A classical baseline, and

A quantum-inspired approach.

# Phase 1 — Classical Brute-Force Optimization

In the first phase, we implement a classical brute-force optimization method.
This exhaustive search examines all possible patient assignments and trip permutations within the specified capacity constraint, ensuring the discovery of the globally optimal solution.

Although computationally expensive for larger instances, this phase serves as a benchmark for validating and comparing the performance of quantum techniques.

# Phase 2 — Quantum-Inspired Optimization (QUBO Formulation)

In the second phase, we reformulate the problem as a Quadratic Unconstrained Binary Optimization (QUBO) model.
This representation allows us to leverage quantum and quantum-inspired solvers.

This phase is further divided into two components:

# Quantum Annealing

Solved using D-Wave libraries, where the annealing process searches for low-energy states that correspond to near-optimal routing plans.

# Quantum Approximate Optimization Algorithm (QAOA)

Implemented in a gate-based quantum framework, where QAOA iteratively optimizes parameterized quantum circuits to approximate the optimal solution.
