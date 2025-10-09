# ⚛️ Alexandria Quantum Hackathon 2025: Team 3 Project

## 🔬 Problem 3: Environmental Chemistry — Quantum Modeling of Carbon Capture

### Project Status: Completed (Hackathon Submission)

---

## 🏛️ Event and Context Overview

This project was developed during the Alexandria Quantum Hackathon 2025, Egypt’s inaugural national quantum hackathon.

| Detail | Value |
| :--- | :--- |
| **Dates** | September 3–5, 2025 |
| **Location** | Bibliotheca Alexandrina, Alexandria, Egypt |
| **Organizers** | Bibliotheca Alexandrina, iQafé Academy |
| **Key Supporters** | Open Quantum Institute (OQI), GESDA, CERN, UBS |
| **Core Mission** | Advancing quantum innovation in key sectors (Climate, AI, Healthcare) and fostering the Arab quantum community. |

---

## 🧪 Problem Statement: $\text{CO}_2$ Capture Kinetics

The project addresses the critical environmental issue of carbon capture. Our goal is to analyze the molecular vibrational properties necessary for understanding the reaction kinetics between **Carbon Dioxide ($\text{CO}_2$)** and a simplified amine-based solvent model, **Ammonia ($\text{NH}_3$)**.

### Goal:
To use a **Variational Quantum Eigensolver (VQE)** or similar quantum algorithm to quantify molecular vibrational energies and reaction pathways.

### Execution Platform:
The quantum solution is designed for and executed on **real quantum hardware** via the **IBM Quantum Cloud** resources.

---

## 👥 Team 3: Roles and Responsibilities

Our team's structure was divided to effectively manage the classical simulation, quantum implementation, and comprehensive reporting requirements of the challenge.

| Member Name | Professional Role | Key Responsibilities |
| :--- | :--- | :--- |
| **Dalia El-Masry** | **Technical Lead & Integration Architect** | Project oversight, defining the overall methodology, ensuring alignment between classical and quantum models, and finalizing the Technical Report structure. |
| **Marwan Abdelghaffar** | **Lead Quantum Algorithm Developer** | Designing and implementing the quantum computing model, UCCSD Ansatz selection, Hamiltonian construction, and using **Qiskit** for quantum circuits. |
| **Hossam Magdy** | **Lead Computational Chemist & Modeler** | Developing the classical quantum chemistry model, performing geometry optimizations, calculating ZPE corrections, and generating initial molecular data using **PySCF**. |
| **Ayman Alaa** | **Quantum Implementation & QA Specialist** | Managing job submission on **IBM Quantum Runtime**, debugging quantum code, performing noise analysis, and optimizing circuit depth/qubit count. |
| **Samira Saeed** | **Documentation & Metrics Analyst** | Authoring the final Technical Report, compiling comparative analysis between models, and tracking evaluation metrics (e.g., energy accuracy, resource consumption). |

---

## 🛠️ Technical Stack and Deliverables

The project deliverables are structured around two main models and a final report.

### 1. Classical Model Notebook (`classical_model.ipynb`)

This notebook performs traditional *ab initio* calculations to provide ground-truth data and initial parameters.

* **Objective:** Analyze molecular geometries (e.g., $\text{CO}_2$, $\text{NH}_3$, $\text{NH}_2\text{COOH}$), vibrational modes, and reaction energetics.
* **Key Tools:**
    * **PySCF:** Core engine for SCF (RHF) and correlation energy calculations (CCSD).
    * **ASE, geomeTRIC:** Used for geometry optimization and path finding simulations.
* **Key Findings (Snippets):** Includes plotting the potential energy surface for the $\text{NH}_3–\text{CO}_2$ complex and calculating the $\Delta E_{\text{ZPE}}$ corrected reaction energy.

### 2. Quantum Model Notebook (`quantum_model.ipynb`)

This notebook translates the chemical problem into a quantum mechanical simulation.

* **Objective:** Apply a variational quantum algorithm to determine the ground state energy of the molecular system.
* **Key Tools:**
    * **Qiskit / Qiskit IBM Runtime:** Framework for circuit design and execution on IBM quantum backends.
    * **ffsim:** Used to facilitate the encoding of molecular Hamiltonians and operators.
* **Methodology:**
    * **Hamiltonian Mapping:** Encoding the molecular system (e.g., $\text{CO}_2$ orbitals) into qubits.
    * **Ansatz:** Implementation of the **Unitary Coupled Cluster Singles and Doubles (UCCSD)** algorithm, potentially using specialized operators like `UCJOpSpinBalanced`.
    * **Metrics:** Focused on resource evaluation (e.g., $\text{CO}_2$ simulation requiring **26 qubits**).

### 3. Technical Report

The definitive document for the project. It synthesizes the work from both notebooks.

* **Content Focus:** Methodology, summary of tools, quantitative evaluation metrics (qubit count, circuit depth), comparative analysis of classical vs. quantum results, and a discussion of hardware limitations and noise effects.

---

## 📜 Sources and Data

The information and foundation for this project are derived exclusively from the hackathon brief and the team's working files.

| Source Type | Description |
| :--- | :--- |
| **Hackathon Brief** | The text defining the **Alexandria Quantum Hackathon 2025** event, mission, dates, and the specific requirements for **Problem 3**. |
| **`classical_model.ipynb`** | Computational notebook demonstrating the classical quantum chemistry simulation of molecular properties and reaction energetics using PySCF. |
| **`quantum_model.ipynb`** | Computational notebook demonstrating the quantum algorithm implementation (UCCSD/VQE) using Qiskit and ffsim, targeting IBM Quantum execution. |
| **`classical_model (1).ipynb`** | Supplementary classical notebook focused on processing data, including the calculation of Zero-Point Energy (ZPE) corrected reaction energies. |

***

*Let us know if you need any section expanded or refined!*
