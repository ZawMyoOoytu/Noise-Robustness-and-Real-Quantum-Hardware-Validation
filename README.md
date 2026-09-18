# Noise-Robustness-and-Real-Quantum-Hardware-Validation

## Overview

This repository contains the research implementation and experimental artifacts for a systematic evaluation of a **Variational Quantum Classifier (VQC)** under ideal simulation, controlled quantum noise, and execution on real quantum hardware.

The study investigates how noise and hardware execution affect classification performance, prediction stability, and output probabilities. The experimental workflow combines classical machine-learning baselines, quantum feature encoding, VQC training, controlled noise experiments, noise-strength sweeps, and real-device validation.

The repository is designed to support **reproducible quantum machine-learning experimentation** and provide the computational artifacts associated with the corresponding research study.

---

## Research Scope

The experimental pipeline evaluates the VQC across the following execution conditions:

1. **Ideal quantum simulation**
2. **Bit-flip noise**
3. **Phase-flip noise**
4. **Depolarizing noise**
5. **Readout noise**
6. **Real IBM Quantum hardware**

This setup enables comparison between idealized quantum computation, controlled noise environments, and actual hardware execution.

---

## Experimental Workflow

```text
Classical Dataset
       │
       ▼
Classical Preprocessing
       │
       ├── Classical Baselines
       │
       ▼
Quantum Feature Encoding
       │
       ▼
VQC Training
       │
       ├──────────────► Ideal Simulation
       │
       ├──────────────► Noisy Simulation
       │                    │
       │                    └── Noise Robustness Sweep
       │
       └──────────────► Real Quantum Hardware
                            │
                            ▼
                    Hardware Validation
                            │
                            ▼
                 Comparative Analysis
```

---

## Experimental Components

### 1. Classical Preprocessing

The dataset is prepared using classical preprocessing and feature scaling before quantum encoding.

Classical baseline models are also evaluated to provide reference performance for the quantum classifier.

### 2. Quantum Feature Encoding

Preprocessed classical features are mapped into quantum states using the implemented quantum encoding pipeline.

The encoding configuration and generated quantum feature data are included in the repository results.

### 3. Variational Quantum Classifier

A parameterized quantum circuit is trained using a variational optimization procedure.

The experimental configuration includes:

* 4 qubits
* 2 VQC layers
* 16 trainable parameters
* 1,024 measurement shots per evaluation
* 800 training samples
* 200 test samples

### 4. Ideal Simulation

The trained VQC is evaluated using an ideal quantum simulator to establish a reference condition without explicitly introduced noise.

### 5. Controlled Noise Experiments

The classifier is evaluated under multiple noise mechanisms:

* Bit-flip errors
* Phase-flip errors
* Depolarizing errors
* Readout errors

The experiments examine changes in classification accuracy, prediction behavior, and probability distributions as noise conditions vary.

### 6. Noise Robustness Sweep

Noise strength is systematically varied for the implemented noise models.

The resulting measurements are used to characterize the relationship between noise intensity and classifier behavior.

### 7. Real Quantum Hardware Validation

The trained circuit is executed on an IBM Quantum device using the Qiskit IBM Runtime interface.

Hardware experiments provide an empirical comparison between ideal simulation results and execution on an actual superconducting quantum processor.

---

## Repository Structure

```text
.
├── 01_environment.ipynb
├── 02_preprocessing.ipynb
├── 03_classical_baselines.ipynb
├── 04_quantum_encoding.ipynb
├── 05_vqc_training.ipynb
├── 06_ideal_simulation.ipynb
├── 07_noisy_simulation.ipynb
├── 08_noise_robustness_sweep.ipynb
├── IBM Quantum Hardware Evaluation.ipynb
│
├── results/
│   ├── experimental CSV files
│   ├── trained model parameters
│   ├── prediction arrays
│   ├── configuration files
│   └── figures/
│
├── README.md
├── requirements.txt
└── .gitignore
```

The notebooks are provided as **executed research notebooks**, together with generated experimental results and figures.

---

## Reproducibility

The repository includes the main computational artifacts required to reproduce and inspect the experimental analysis, including:

* Executed Jupyter notebooks
* Training history
* Model parameters
* Prediction outputs
* Ideal simulation results
* Noisy simulation results
* Noise robustness sweep results
* Real-hardware evaluation results
* Comparative experimental tables
* Statistical validation outputs
* Publication-oriented figures
* Environment dependency specification

The experiments use fixed configurations and stored outputs where applicable to facilitate reproducibility and independent inspection.

---

## Software Environment

The primary experimental environment uses:

* Python 3.11
* Qiskit 2.5.2
* Qiskit Aer 0.17.2
* Qiskit IBM Runtime 0.49.0
* NumPy 2.4.6
* Pandas 3.0.5
* SciPy 1.17.1
* Scikit-learn 1.9.1
* Matplotlib 3.10.1
* JupyterLab 4.0.11

Exact package versions are specified in:

```text
requirements.txt
```

---

## Real Quantum Hardware

The hardware-validation experiment uses the **IBM Quantum** platform through Qiskit IBM Runtime.

Hardware execution is treated separately from simulator-based experiments. This distinction is important because simulator noise models and physical quantum-device behavior are not equivalent.

The hardware notebook records the experimental configuration and generated results used for the comparative analysis.

> **Note:** Real-device availability, backend status, calibration characteristics, queue conditions, and hardware noise can change over time. Therefore, hardware results should be interpreted as measurements from the recorded experimental execution rather than as permanent device characteristics.

---

## Results and Analysis

The `results/` directory contains generated experimental artifacts used for comparative evaluation.

These include analyses of:

* Classification accuracy
* F1 score
* Prediction stability
* Probability stability
* Prediction-change rate
* Noise impact
* Noise robustness
* Ideal-versus-hardware behavior
* Hardware probability shifts
* Confusion matrices
* Bootstrap confidence intervals
* Statistical validation

The accompanying figures provide visual representations of the experimental comparisons.

---

## Security and Credentials

No API keys, access tokens, passwords, or private credentials are intentionally included in this repository.

IBM Quantum authentication must be configured **locally**.

Credentials should never be hard-coded into notebooks, source files, or Git commits.

For example, authentication information should be supplied through a secure local configuration mechanism rather than committed to the repository.

If credentials have previously been exposed in a Git repository, they should be revoked and replaced immediately.

---

## Research Status

**Status:** Research prototype / experimental research implementation.

This repository represents an experimental research artifact supporting ongoing work in:

* Quantum Machine Learning
* Variational Quantum Algorithms
* Noise-Robust Quantum Computing
* Quantum Hardware Validation
* Trustworthy AI
* Hardware-aware Quantum AI

The implementation and experimental results are intended for research, analysis, reproducibility, and further methodological development.

---

## Citation

If you use this repository, experimental implementation, or derived results in academic work, please cite the associated research publication when available.

A formal citation file and publication metadata may be added as the research work progresses.

---

## License

A formal open-source license will be specified separately.

Until a license is added, the repository should not be assumed to grant unrestricted permission to redistribute, modify, or commercially use the research artifacts.

---

## Author

**Zaw Myo Oo**

Freelance Technology Researcher

Research interests include Quantum AI, Quantum Machine Learning, trustworthy AI, noise-aware algorithms, and intelligent communication systems.
