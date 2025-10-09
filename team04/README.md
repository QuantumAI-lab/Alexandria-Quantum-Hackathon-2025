# Smart Traffic Optimization in the New Administrative Capital

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Quantum Computing](https://img.shields.io/badge/Quantum-QAOA-blue.svg)](https://qiskit.org/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)

**2025 Alexandria Quantum Hackathon - Team 04**

A hybrid quantum-classical optimization framework for emergency vehicle routing in Egypt's New Administrative Capital, designed to minimize response times and save lives through intelligent traffic management.

---

## 🚑 Overview

Emergency response time is a critical determinant of survival in urgent medical situations. Research shows that survival rates drop from **19.5% to 9.4%** when emergency medical services arrive after 10 minutes instead of within 6 minutes. This project applies quantum computing and classical optimization techniques to solve the **Capacitated Vehicle Routing Problem (CVRP)** for ambulance dispatch, dramatically reducing travel times in congested urban environments.

### Key Impact
- **Each minute saved**: ~6.4% improvement in survival likelihood
- **Target**: Optimal multi-patient pickup routes with capacity constraints
- **Approach**: Quantum annealing, QAOA, and hybrid classical-quantum algorithms

---

## 🎯 Problem Statement

**Scenario**: Five patients require urgent hospital transport. One ambulance is available.

**Constraints**:
- Maximum 3 patients per trip
- Ambulance can make multiple trips
- All patients must reach the hospital
- Minimize total travel distance

**Mathematical Formulation**: Shortest path on a directed weighted graph with capacity constraints, formulated as a QUBO (Quadratic Unconstrained Binary Optimization) problem for quantum devices.

---

## 🔬 Technical Approach

### Classical Solutions
We implemented and benchmarked multiple classical algorithms:

| Algorithm | Distance (km) | Runtime (s) |
|-----------|---------------|-------------|
| Brute Force | 57.311 | 0.0006 |
| A* Search | 57.311 | 0.0008 |
| OR-Tools | 57.311 | 0.0211 |
| Heuristic | 57.311 | 0.0001 |

### Quantum Solutions
Developed **12 different QUBO formulations** ranging from 5 to 180 qubits:

#### Core Formulations
- **180 Qubits**: Full CVRP encoding (theoretical)
- **60 Qubits**: Two-trip hypothesis
- **35/45 Qubits**: Complete constraint encoding with/without ancilla variables
- **30 Qubits**: Main practical implementation (reference model)
- **14 Qubits**: Binary slack variables for capacity
- **12 Qubits**: Hybrid quantum-classical decomposition
- **10 Qubits**: Assignment-based encoding
- **5 Qubits**: Minimal pruned set-partitioning

### Quantum Hardware Results

Tested on **IBM Quantum** (`ibm_kingston`, `ibm_pittsburgh`) with 2048 shots:

| Success Rate | Best Distance | Optimal Solution |
|--------------|---------------|------------------|
| 31.6% (6/19 runs) | **57.5244 km** | Trip 1: H→DT→GR→IT→H (3 patients)<br>Trip 2: H→R3_2→R2→H (2 patients) |

**Key Findings**:
- Quantum solutions matched classical optimal in successful runs
- Execution time: 60s - 2600s (hardware-dependent)
- Primary challenge: Constraint violation in noisy intermediate-scale quantum (NISQ) devices
- Hybrid approaches showed most promise for near-term deployment

---

## 📊 Repository Structure

```
team04/
├── AQH/
│   ├── evidence/          # Experimental logs and validation
│   ├── logs/              # Execution logs and telemetry
│   ├── results/           # Output data and solution files
│   └── screenshots/       
├── notebooks/
│   ├── 5_Qubits.ipynb            # Minimal pruned formulation
│   ├── 10_Qubits.ipynb           # Assignment-based encoding
│   ├── 12_Qubits.ipynb           # Hybrid decomposition
│   ├── 14_Qubits.ipynb           # Slack variable approach
│   ├── 14_Qubits_Hardware.ipynb  # IBM hardware implementation
│   ├── 30QubitQAOA_QiskitHardware.ipynb  # model that run on real hardware
│   ├── 30_Qubits_Hardware(Another_Approach).ipynb # another apporach that we tried
│   ├── 30_Qubits(issues).ipynb   # ,ain 30 qubit apporach but it didn't run correctly
│   └── Classical.ipynb           # Baseline algorithms
├── requirements/          # Dependency specifications
│   ├── requirements.txt          # All packages (full install)
│   ├── requirements-classical.txt    # For Classical.ipynb
│   ├── requirements-5qubits.txt      # For 5_Qubits.ipynb
│   ├── requirements-10qubits.txt     # For 10_Qubits.ipynb
│   ├── requirements-12qubits.txt     # For 12_Qubits.ipynb
│   ├── requirements-14qubits.txt     # For 14_Qubits.ipynb
│   ├── requirements-30qubits.txt     # For 30_Qubits.ipynb
│   └── requirements-hardware.txt     # For hardware notebooks
├── documentation.pdf      # Full technical report (28 pages)
├── presentation.pptx      # Hackathon presentation slides
├── job_ids1.csv          # IBM Quantum job tracking
├── MANIFEST_1.json       # Configuration metadata
└── MIT License           # Open source license
```

---

## 🚀 Getting Started

### Prerequisites
```bash
Python 3.8+
Jupyter Notebook or JupyterLab
IBM Quantum Experience account (for hardware runs)
```

### Installation Options

#### Option 1: Install All Dependencies (Recommended)
```bash
# Clone the repository
git clone https://github.com/QuantumAI-lab/Alexandria-Quantum-Hackathon-2025.git
cd Alexandria-Quantum-Hackathon-2025/team04

# Install all packages for all notebooks
pip install -r requirements/requirements.txt
```

#### Option 2: Install Per-Notebook Dependencies
Each notebook has its own requirements file. Install only what you need:

```bash
# For classical algorithms only
pip install -r requirements/requirements-classical.txt

# For 30-qubit quantum implementation (main model)
pip install -r requirements/requirements-30qubits.txt

# For hardware execution on IBM Quantum
pip install -r requirements/requirements-hardware.txt

# For specific qubit formulations
pip install -r requirements/requirements-5qubits.txt
pip install -r requirements/requirements-10qubits.txt
pip install -r requirements/requirements-12qubits.txt
pip install -r requirements/requirements-14qubits.txt
```

### Notebook-Specific Requirements

| Notebook | Requirements File | Key Packages |
|----------|------------------|--------------|
| `Classical.ipynb` | `requirements-classical.txt` | numpy, scipy, ortools, matplotlib |
| `5_Qubits.ipynb` | `requirements-5qubits.txt` | qiskit, qiskit-aer, numpy |
| `10_Qubits.ipynb` | `requirements-10qubits.txt` | qiskit, qiskit-algorithms, matplotlib |
| `12_Qubits.ipynb` | `requirements-12qubits.txt` | qiskit, qiskit-algorithms, scipy |
| `14_Qubits.ipynb` | `requirements-14qubits.txt` | qiskit, qiskit-optimization, networkx |
| `30_Qubits.ipynb` | `requirements-30qubits.txt` | qiskit, qiskit-optimization, matplotlib |
| `*_Hardware.ipynb` | `requirements-hardware.txt` | qiskit-ibm-runtime, all quantum packages |

### Quick Start

#### Run Classical Baseline
```bash
jupyter notebook AQH/Classical.ipynb
```

#### Run Main Quantum Model (30 Qubits - Simulator)
```bash
pip install -r requirements/requirements-30qubits.txt
jupyter notebook AQH/30_Qubits.ipynb
```

#### Execute on IBM Hardware
```bash
pip install -r requirements/requirements-hardware.txt
# Configure IBM Quantum API token in notebook
jupyter notebook AQH/30_Qubits_Hardware.ipynb
```

### Setting Up IBM Quantum Access

For hardware notebooks, you need an IBM Quantum account:

1. Create account at [quantum.ibm.com](https://quantum.ibm.com/)
2. Get your API token from the dashboard
3. Add to notebook:
```python
from qiskit_ibm_runtime import QiskitRuntimeService

# Save credentials (first time only)
QiskitRuntimeService.save_account(channel="ibm_quantum", token="YOUR_TOKEN")

# Load service
service = QiskitRuntimeService()
```

---

## 📈 Results Summary

### Classical vs Quantum

| Aspect | Classical | Quantum (QAOA) |
|--------|-----------|----------------|
| **Solution Quality** | Guaranteed optimal (MILP) | High-quality when feasible |
| **Best Distance** | 57.311 km | 57.5244 km |
| **Runtime** | 0.001s - 0.021s | 60s - 2600s |
| **Robustness** | 100% constraint satisfaction | 31.6% on real hardware |
| **Scalability** | Mature for medium instances | Limited by qubit count |

### Hybrid Recommendation
For **production deployment**: Use classical solvers for reliability.  
For **research advancement**: Continue quantum/hybrid exploration with:
1. Automated penalty calibration
2. Problem decomposition strategies
3. Classical post-processing to repair infeasible quantum samples

---

## 🛠️ Development Notes

### Creating Virtual Environment (Recommended)
```bash
# Create virtual environment
python -m venv venv

# Activate
# On Linux/Mac:
source venv/bin/activate
# On Windows:
venv\Scripts\activate

# Install dependencies
pip install -r requirements/requirements.txt
```

### Troubleshooting

**Issue**: `ImportError: No module named 'qiskit'`  
**Solution**: Install quantum requirements: `pip install -r requirements/requirements-30qubits.txt`

**Issue**: Hardware jobs timing out  
**Solution**: Check IBM Quantum queue status at [quantum.ibm.com](https://quantum.ibm.com/). Consider using simulator for testing.

**Issue**: QAOA convergence failures  
**Solution**: Adjust penalty weights in QUBO formulation or increase QAOA depth parameter.

---

## 🏆 Team

**Team Members**:
- Bassel Ahmed
- Mohamed Abo-Zeid
- Omar Ayoub
- Hassan Khalifa
- Youssef Rezk

**Mentors**:
- Ahmed Saad El Fiky
- James Austin Myer

---

## 📚 Key References

1. **AIMMS** - Capacitated Vehicle Routing Problem: Formulation (Linear Integer Programming), 2024
2. **Glover et al.** - A Tutorial on Formulating and Using QUBO Models, arXiv:1811.11538, 2018
3. **Ibrahim et al.** - Capacitated Vehicle Routing with Column Generation and Reinforcement Learning, 2020

Full bibliography available in [`documentation.pdf`](./documentation.pdf)

---

## 📄 License

This project is licensed under the MIT License - see the [MIT License](./MIT%20License) file for details.

---

## 🔗 Links

- **Competition**: [Alexandria Quantum Hackathon 2025](https://github.com/QuantumAI-lab/Alexandria-Quantum-Hackathon-2025)
- **IBM Quantum**: [Qiskit Documentation](https://qiskit.org/documentation/)
- **Qiskit Tutorials**: [Learn Quantum Computing](https://qiskit.org/learn)
- **Full Report**: [documentation.pdf](./documentation.pdf)

---

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Install dependencies for affected notebooks
4. Test your changes
5. Submit a pull request

---

## 📧 Contact

For questions or collaboration opportunities, please open an issue or contact the team through the hackathon organizers.

---

<div align="center">

**Built with quantum computing to save lives** 🚑⚛️

*Developed during the 2025 Alexandria Quantum Hackathon*

</div>