# Noise Robustness and Real Quantum Hardware Validation

## Overview

This repository contains the research implementation, experimental data, analysis outputs, and publication-oriented artifacts for a systematic evaluation of a **Variational Quantum Classifier (VQC)** under ideal simulation, controlled quantum noise, and execution on real quantum hardware.

The study investigates how different noise mechanisms and physical hardware execution affect quantum-classification performance, prediction stability, and output probability distributions.

The experimental workflow integrates classical machine-learning baselines, quantum feature encoding, variational circuit training, controlled noise experiments, noise-strength sweeps, and real-device execution.

The repository is intended to support **reproducible quantum machine-learning experimentation**, independent inspection of experimental results, and further methodological development.

---

## Research Objectives

The experimental study focuses on four main objectives:

1. Establish a reference VQC performance under ideal quantum simulation.
2. Quantify the effect of controlled noise models on classification behavior.
3. Characterize classifier robustness as noise strength is varied.
4. Compare simulator-based results with measurements obtained from real quantum hardware.

The evaluation considers not only classification accuracy, but also prediction stability and changes in output probability distributions.

---

## Experimental Scope

The VQC is evaluated under the following execution conditions:

1. **Ideal quantum simulation**
2. **Bit-flip noise**
3. **Phase-flip noise**
4. **Depolarizing noise**
5. **Readout noise**
6. **Combined noise conditions**
7. **Real IBM Quantum hardware**

This experimental design provides a progression from an idealized computational reference to controlled noisy environments and finally to physical quantum-device execution.

---

## Experimental Workflow

```text
                    Classical Dataset
                           │
                           ▼
                Classical Preprocessing
                           │
             ┌─────────────┴─────────────┐
             │                           │
             ▼                           ▼
     Classical Baselines          Quantum Feature Encoding
                                         │
                                         ▼
                                  VQC Training
                                         │
                  ┌──────────────────────┼──────────────────────┐
                  │                      │                      │
                  ▼                      ▼                      ▼
           Ideal Simulation      Noisy Simulation       Real Quantum
                                        │                 Hardware
                                        ▼                      │
                              Noise Robustness Sweep           │
                                        │                      │
                                        └──────────┬───────────┘
                                                   ▼
                                         Comparative Analysis
                                                   │
                                                   ▼
                                      Statistical Validation
```

---

## Experimental Components

### 1. Classical Preprocessing

The dataset is processed using classical preprocessing and feature-scaling procedures before quantum encoding.

Classical machine-learning baselines are evaluated separately to provide reference performance against which the VQC results can be interpreted.

---

### 2. Quantum Feature Encoding

The preprocessed classical features are transformed into quantum representations using the implemented quantum feature-encoding pipeline.

The corresponding encoding configuration and generated experimental data are retained in the repository where applicable.

---

### 3. Variational Quantum Classifier

The quantum classifier uses a parameterized variational circuit optimized through a classical optimization procedure.

The primary experimental configuration includes:

| Configuration        | Value |
| -------------------- | ----: |
| Qubits               |     4 |
| VQC layers           |     2 |
| Trainable parameters |    16 |
| Measurement shots    | 1,024 |
| Training samples     |   800 |
| Test samples         |   200 |

These values describe the reported experimental configuration and may be modified for future experiments.

---

### 4. Ideal Quantum Simulation

The trained VQC is first evaluated using an ideal quantum simulator.

This experiment establishes the reference behavior against which noisy simulation and real-hardware measurements are compared.

No explicitly introduced quantum noise model is applied in the ideal reference experiment.

---

### 5. Controlled Noise Experiments

The classifier is evaluated under several controlled noise mechanisms:

* Bit-flip errors
* Phase-flip errors
* Depolarizing errors
* Readout errors
* Combined noise conditions

The experiments investigate changes in:

* Classification accuracy
* F1 score
* Prediction stability
* Prediction-change rate
* Output probability distributions
* Noise-induced performance degradation

---

### 6. Noise Robustness Sweep

Noise strength is systematically varied across the implemented noise models.

The resulting measurements are used to characterize the relationship between noise intensity and classifier behavior.

The sweep experiments provide quantitative data for evaluating:

* Performance degradation
* Prediction instability
* Probability shifts
* Robustness trends
* Differences between noise mechanisms

---

### 7. Real Quantum Hardware Validation

The trained circuit is executed on an IBM Quantum device through the **Qiskit IBM Runtime** interface.

The hardware experiment provides an empirical comparison between simulator-based expectations and physical quantum-device measurements.

Hardware execution is analyzed separately from simulator experiments because simulated noise models and the behavior of a physical quantum processor are not equivalent.

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
│   ├── ideal results
│   ├── noise-model results
│   ├── robustness-sweep results
│   ├── hardware evaluation results
│   └── comparative analysis data
│
├── paper_figures/
│   ├── experimental dashboards
│   ├── noise robustness figures
│   ├── hardware comparison figures
│   ├── probability analysis figures
│   └── statistical validation figures
│
├── README.md
├── requirements.txt
└── .gitignore
```

The notebooks are maintained as **executed research notebooks** where applicable, together with generated numerical results and publication-oriented figures.

---

## Reproducibility

The repository contains the principal computational artifacts required to inspect and reproduce the experimental workflow, including:

* Executed Jupyter notebooks
* Experimental configurations
* Training outputs
* Model parameters
* Prediction outputs
* Ideal simulation results
* Controlled-noise simulation results
* Noise robustness sweep results
* Real-hardware evaluation results
* Comparative analysis tables
* Statistical validation outputs
* Publication-oriented figures
* Environment dependency specifications

Where applicable, fixed configurations and stored experimental outputs are provided to facilitate independent inspection and reproducibility.

Because real quantum hardware is subject to changing calibration conditions, queue states, backend availability, and device noise, hardware experiments should be interpreted together with their recorded execution context.

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

The dependency configuration is maintained in:

```text
requirements.txt
```

To create the experimental environment:

```bash
pip install -r requirements.txt
```

Additional system-level configuration may be required depending on the local Python and Jupyter installation.

---

## Real Quantum Hardware

The hardware-validation experiments use the **IBM Quantum** platform through Qiskit IBM Runtime.

The hardware execution is treated as a separate experimental condition from ideal and simulated-noise experiments.

This distinction is important because:

```text
Ideal Simulation
      │
      ├── controlled computational reference
      │
      ▼
Noisy Simulation
      │
      ├── explicitly defined noise models
      │
      ▼
Real Quantum Hardware
      │
      └── physical device behavior
```

Real-device results should therefore not be interpreted simply as another predefined simulator noise model.

### Hardware Considerations

Real quantum-device behavior may vary because of:

* Device calibration
* Gate errors
* Readout errors
* Qubit connectivity
* Circuit transpilation
* Backend configuration
* Queue and execution conditions
* Temporal changes in hardware noise

Consequently, hardware measurements reported by this repository represent observations from the recorded experimental executions rather than permanent characteristics of a particular quantum processor.

---

## Results and Analysis

The `results/` directory contains generated numerical artifacts used for experimental analysis.

The current analysis includes measurements related to:

* Classification accuracy
* F1 score
* Prediction stability
* Prediction-change rate
* Output probability stability
* Probability shifts
* Noise-induced performance changes
* Noise robustness
* Ideal-versus-hardware comparison
* Confusion matrices
* Bootstrap confidence intervals
* Statistical validation

The `paper_figures/` directory contains visualizations generated from the experimental results for research analysis and potential publication use.

---

## Experimental Interpretation

The experiments are designed to distinguish three related but different questions:

### Question 1 — What is the classifier capable of under ideal conditions?

The ideal simulation establishes the reference behavior of the trained VQC without explicitly introduced noise.

### Question 2 — How does controlled noise affect the classifier?

The noisy simulations isolate specific noise mechanisms and examine how increasing noise strength changes classification and probability behavior.

### Question 3 — How does the trained circuit behave on physical hardware?

The real-device experiment provides measurements from an actual quantum processor and enables comparison with the corresponding simulator-based results.

This separation helps avoid treating simulated noise behavior and physical hardware behavior as interchangeable experimental conditions.

---

## Security and Credentials

No API keys, access tokens, passwords, or private credentials are intentionally included in this repository.

IBM Quantum authentication must be configured locally.

Credentials should never be hard-coded into notebooks, source files, configuration files, or Git commits.

Authentication information should instead be supplied through an appropriate secure local configuration mechanism.

If credentials have previously been exposed in a repository, they should be revoked and replaced immediately.

---

## Research Status

**Status:** Research prototype / experimental research implementation

This repository supports ongoing research in:

* Quantum Machine Learning
* Variational Quantum Algorithms
* Noise-Robust Quantum Computing
* Quantum Hardware Validation
* Hardware-Aware Quantum AI
* Trustworthy AI
* Noise-Aware Algorithmic Intelligence

The implementation is intended for research experimentation, quantitative analysis, reproducibility, and further methodological development.

The repository should be considered an evolving research artifact rather than a production software package.

---

## Limitations

The current experimental results should be interpreted within the scope of the implemented dataset, circuit architecture, noise models, hardware configuration, and experimental settings.

In particular:

* The VQC configuration uses a relatively small number of qubits.
* Simulated noise models represent controlled abstractions of quantum errors.
* Real-device measurements depend on the selected backend and its time-varying calibration state.
* Hardware results may not generalize to other quantum processors.
* Experimental conclusions are limited to the evaluated dataset and model configuration unless further experiments establish broader generality.

These limitations provide directions for future experimental extensions.

---

## Future Research Directions

Potential extensions include:

* Larger quantum circuits
* Additional quantum datasets
* Alternative feature-encoding strategies
* Additional VQC architectures
* More comprehensive noise models
* Error mitigation techniques
* Cross-backend hardware evaluation
* Repeated hardware experiments under different calibration conditions
* Hardware-aware circuit optimization
* Larger statistical evaluation
* Comparative evaluation with additional quantum-classical models

---

## Citation

If you use this repository, its implementation, experimental data, figures, or derived results in academic work, please cite the associated research publication when available.

A formal citation file and complete publication metadata may be added as the research work progresses.

---

## License

A formal open-source license will be specified separately.

Until a license is added, this repository should **not** be interpreted as granting unrestricted permission to redistribute, modify, or commercially use the research artifacts.

---

## Author

**Zaw Myo Oo**

Freelance Technology Researcher

Research interests include:

* Quantum AI
* Quantum Machine Learning
* Variational Quantum Algorithms
* Noise-Aware Algorithms
* Trustworthy AI
* Intelligent Communication Systems
* Quantum-Assisted AI for Next-Generation Networks
