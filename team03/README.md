# ⚛️ Alexandria Quantum Hackathon 2025 Project: Problem 3

## 🌍 Environmental Chemistry: Carbon Capturing Process

Welcome to the project repository for Team 3's solution developed during the **Alexandria Quantum Hackathon 2025**. This project tackles a critical environmental challenge by leveraging the power of quantum computing.

---

## 🏛️ Event Overview

This event marks Egypt’s debut on the global quantum innovation map, organized by the Bibliotheca Alexandrina and iQafé Academy, with strategic support from the Open Quantum Institute (OQI).

| Detail | Value |
| :--- | :--- |
| **Dates** | September 3–5, 2025 |
| **Location** | Bibliotheca Alexandrina, Alexandria, Egypt |
| **Languages** | Arabic & English |
| **Organizers** | Bibliotheca Alexandrina, iQafé Academy |
| **Key Supporters** | Open Quantum Institute (OQI), GESDA, CERN, UBS |
| **Mission Focus** | Advancing quantum innovation across climate, AI, healthcare, and building the Arab quantum community. |

---

## 🔬 Problem Statement: Quantifying $\text{CO}_2$ Capture

**Problem 3:** Environmental chemistry; carbon capturing process

Carbon capturing processes are crucial for mitigating climate change. Understanding the **molecular vibrational properties** is essential for determining reaction kinetics.

### Solution Goal:
Use a **Variational Quantum Eigensolver (VQE)** or a similar quantum algorithm to quantify molecular vibrational energies and reaction pathways between $\text{CO}_2$ and a simplified amine-based solvent model, **$\text{NH}_3$**.

### Execution Requirement:
The solution must be executed on **real quantum hardware** using **IBM Quantum cloud resources**.

---

## 🧑‍💻 Team Members

| Name | Role / Focus |
| :--- | :--- |
| **Marwan Abdelghaffar** | *Team Member* |
| **Hossam Magdy** | *Team Member* |
| **Ayman Alaa** | *Team Member* |
| **Dalia El-Masry** | *Team Member* |
| **Samira Saeed** | *Team Member* |

---

## 📦 Deliverables and Project Structure

The project is divided into three primary deliverables, available in this repository:

1.  **Classical Model Notebook**
2.  **Quantum Model Notebook**
3.  **Technical Report** (Methodology Summary)

### 1. Classical Model Notebook (`classical_model.ipynb`)

This notebook demonstrates the conventional quantum chemistry approach to the problem.

* **Objective:** Analyze molecular geometries, vibrational modes, and reaction energetics for the $\text{CO}_2$ + $\text{NH}_3$ system, often focusing on the carbamic acid intermediate ($\text{NH}_2\text{COOH}$).
* **Key Tools:** **PySCF** (for SCF and CCSD calculations), **ASE**, **geomeTRIC**.
* **Calculations Included:** Geometry optimization, calculation of electronic and zero-point energy (ZPE) corrected reaction energies.

### 2. Quantum Model Notebook (`quantum_model.ipynb`)

This notebook implements the quantum algorithm to simulate the molecular properties.

* **Objective:** Apply a variational algorithm to find the ground state energy of the molecular system.
* **Key Tools:** **Qiskit**, **IBM Quantum Runtime**, **PySCF**, **ffsim**.
* **Methodology:**
    * **Hamiltonian Construction** using PySCF to generate fermionic operators.
    * **Ansatz Design:** Employing the **Unitary Coupled Cluster with Singles and Doubles (UCCSD)** ansatz, often using a spin-balanced form (e.g., `UCJOpSpinBalanced`).
    * **Execution:** Circuit design and submission for execution on **IBM Quantum backends**.

### 3. Technical Report

A comprehensive document outlining the methodology and results.

* **Content:**
    * Conceptual overview of the modeling approach.
    * Summary of tools and frameworks used (Qiskit, PySCF, etc.).
    * Evaluation metrics (e.g., **circuit depth**, **qubit count**, and **energy accuracy**).
    * Comparative analysis of simulation results (Classical vs. Quantum).
    * Discussion of limitations and **noise effects** observed during quantum hardware execution.

---

## 🔗 Key Resources & Contacts

| Resource | Contact/Link |
| :--- | :--- |
| **Bibliotheca Alexandrina** (Host) | [BA Website](http://www.bibalex.org) |
| **iQafé Academy** (Partner) | *Link TBD* |
| **Media & Partnerships** | `quantum@bibalex.org` |
