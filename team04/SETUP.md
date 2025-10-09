# Setup Guide

This guide helps you install the correct dependencies for running specific notebooks in the Smart Traffic Optimization project.

## Quick Reference

| Notebook | Requirements File | Install Command |
|----------|------------------|-----------------|
| All notebooks | `requirements.txt` | `pip install -r requirements/requirements.txt` |
| Classical.ipynb | `requirements-classical.txt` | `pip install -r requirements/requirements-classical.txt` |
| 5_Qubits.ipynb | `requirements-5qubits.txt` | `pip install -r requirements/requirements-5qubits.txt` |
| 10_Qubits.ipynb | `requirements-10qubits.txt` | `pip install -r requirements/requirements-10qubits.txt` |
| 12_Qubits.ipynb | `requirements-12qubits.txt` | `pip install -r requirements/requirements-12qubits.txt` |
| 14_Qubits.ipynb | `requirements-14qubits.txt` | `pip install -r requirements/requirements-14qubits.txt` |
| 30_Qubits.ipynb | `requirements-30qubits.txt` | `pip install -r requirements/requirements-30qubits.txt` |
| *_Hardware.ipynb | `requirements-hardware.txt` | `pip install -r requirements/requirements-hardware.txt` |

## Installation Methods

### Method 1: Install Everything (Recommended for Development)

```bash
cd team04
pip install -r requirements/requirements.txt
```

This installs all dependencies needed for all notebooks.

### Method 2: Per-Notebook Installation (Lightweight)

Install only what you need for specific notebooks:

#### For Classical Algorithms Only
```bash
pip install -r requirements/requirements-classical.txt
jupyter notebook AQH/Classical.ipynb
```

#### For Main Quantum Model (30 Qubits)
```bash
pip install -r requirements/requirements-30qubits.txt
jupyter notebook AQH/30_Qubits.ipynb
```

#### For IBM Quantum Hardware
```bash
pip install -r requirements/requirements-hardware.txt
jupyter notebook AQH/30_Qubits_Hardware.ipynb
```

## Virtual Environment Setup (Recommended)

### Linux/Mac
```bash
# Create virtual environment
python3 -m venv quantum-env

# Activate
source quantum-env/bin/activate

# Install dependencies
pip install -r requirements/requirements.txt
```

### Windows
```bash
# Create virtual environment
python -m venv quantum-env

# Activate
quantum-env\Scripts\activate

# Install dependencies
pip install -r requirements/requirements.txt
```

## IBM Quantum Hardware Setup

To run notebooks on real quantum hardware:

### 1. Create IBM Quantum Account
- Visit [quantum.ibm.com](https://quantum.ibm.com/)
- Sign up for a free account
- Access the dashboard

### 2. Get API Token
- Navigate to your account settings
- Copy your API token

### 3. Configure in Notebook
Add this at the beginning of hardware notebooks:

```python
from qiskit_ibm_runtime import QiskitRuntimeService

# First time only - save credentials
QiskitRuntimeService.save_account(
    channel="ibm_quantum",
    token="YOUR_API_TOKEN_HERE"
)

# For subsequent runs - load service
service = QiskitRuntimeService()
backend = service.backend("ibm_kingston")  # or ibm_pittsburgh
```

## Package Details

### Core Dependencies
- **numpy**: Numerical computing
- **scipy**: Scientific algorithms
- **matplotlib**: Plotting and visualization
- **pandas**: Data manipulation

### Quantum Computing
- **qiskit**: IBM's quantum computing framework
- **qiskit-aer**: Local quantum simulator
- **qiskit-algorithms**: Quantum algorithms (QAOA, VQE)
- **qiskit-optimization**: QUBO formulation tools
- **qiskit-ibm-runtime**: Access to real IBM hardware

### Classical Optimization
- **ortools**: Google's optimization library (MILP, CP)

### Graph Analysis
- **networkx**: Graph algorithms (for routing)

## Troubleshooting

### Issue: ImportError for qiskit modules
**Solution**: Ensure you're using compatible versions
```bash
pip install --upgrade qiskit qiskit-aer qiskit-algorithms
```

### Issue: OR-Tools installation fails
**Solution**: Install build tools first
```bash
# Ubuntu/Debian
sudo apt-get install python3-dev

# Mac
brew install python

# Then retry
pip install ortools
```

### Issue: Jupyter kernel not found
**Solution**: Register the kernel
```bash
python -m ipykernel install --user --name=quantum-env
```

### Issue: IBM Quantum authentication fails
**Solution**: Clear and re-save credentials
```python
from qiskit_ibm_runtime import QiskitRuntimeService
QiskitRuntimeService.delete_account()
QiskitRuntimeService.save_account(channel="ibm_quantum", token="NEW_TOKEN")
```

## Verification

Test your installation:

```python
# Test classical packages
import numpy as np
import scipy
from ortools.constraint_solver import routing_enums_pb2
print("Classical packages: OK")

# Test quantum packages
import qiskit
from qiskit_aer import AerSimulator
from qiskit_algorithms.minimum_eigensolvers import QAOA
print("Quantum packages: OK")

# Test hardware access (requires API token)
from qiskit_ibm_runtime import QiskitRuntimeService
service = QiskitRuntimeService()
print("IBM Quantum access: OK")
```

## Updating Dependencies

To update all packages to latest compatible versions:

```bash
pip install --upgrade -r requirements/requirements.txt
```

To update specific package:
```bash
pip install --upgrade qiskit
```

## Uninstallation

To remove the virtual environment:

```bash
# Deactivate first
deactivate

# Remove directory
rm -rf quantum-env  # Linux/Mac
rmdir /s quantum-env  # Windows
```

## Support

For issues or questions:
1. Check [Qiskit documentation](https://qiskit.org/documentation/)
2. Visit [IBM Quantum support](https://quantum.ibm.com/support)
3. Open an issue in the repository

## Version Information

Tested with:
- Python 3.8, 3.9, 3.10, 3.11
- Qiskit 0.45+
- IBM Quantum backends: ibm_kingston, ibm_pittsburgh
- Last updated: January 2025