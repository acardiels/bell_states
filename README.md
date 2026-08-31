# Bell State Generator

A Python project (built on [Qiskit](https://qiskit.org/)) for constructing, simulating, and visualizing the four Bell states through quantum circuits. It includes both an interactive Jupyter notebook for step-by-step exploration and an executable terminal script for generating the circuits, the resulting states, and their graphical representations.

## Table of Contents

- [Description](#description)
- [Theoretical Background](#theoretical-background)
- [Repository Structure](#repository-structure)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
  - [Jupyter Notebook](#jupyter-notebook)
  - [Terminal Script](#terminal-script)
- [Generated Images](#generated-images)
- [Example Results](#example-results)
- [Contributing](#contributing)
- [License](#license)

## Description

**Bell states** are the four maximally entangled two-qubit states and one of the most fundamental examples of quantum entanglement. This project implements the quantum circuits needed to prepare each of these states, simulates their execution, and automatically saves:

- The **quantum circuit** used to generate the state.
- A **measurement of the resulting state** .

The code is designed for both interactive exploration (Jupyter) and reproducible command-line use (script in `/src`).

## Theoretical Background

The four Bell states are obtained by applying a Hadamard gate (H) to the first qubit followed by a CNOT gate controlled by that qubit on the second, starting from different initial states:

| State | Notation | Expression |
|---|---|---|
| Φ⁺ | `phi_plus` | (\|00⟩ + \|11⟩) / √2 |
| Φ⁻ | `phi_minus` | (\|00⟩ − \|11⟩) / √2 |
| Ψ⁺ | `psi_plus` | (\|01⟩ + \|10⟩) / √2 |
| Ψ⁻ | `psi_minus` | (\|01⟩ − \|10⟩) / √2 |

Each one is obtained from `Φ⁺` by applying additional gates (X and/or Z) before the CNOT gate, following the standard construction of entanglement circuits.

## Repository Structure

```
.
├── README.md                  # This document
├── requirements.txt            # Project dependencies
├── .venv/                      # Python virtual environment (not versioned)
├── notebook.ipynb               # Interactive notebook with step-by-step explanation and execution
├── src/
│   └── bell_states.py           # Executable terminal script
└── images/
    ├── circuits/                 # Diagrams of the generated quantum circuits
    └── measurements/             # State measurements of every Bell state 
```

> **Note:** the exact file names (`notebook.ipynb`, `src/bell_states.py`) can be adjusted to match the ones actually used in your repository; update these paths if they differ.

## Requirements

- Python 3.9 or higher
- [Qiskit](https://qiskit.org/) and its visualization dependencies
- Jupyter Notebook / JupyterLab (for the interactive notebook)

All exact dependencies are pinned in [`requirements.txt`](./requirements.txt).

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   cd <repo-name>
   ```

2. Create and activate a virtual environment:

   ```bash
   python -m venv .venv

   # Linux / macOS
   source .venv/bin/activate

   # Windows
   .venv\Scripts\activate
   ```

3. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

## Usage

### Jupyter Notebook

The included notebook provides a guided exploration of how each Bell state is constructed, letting you visualize its circuit and resulting state, and interactively tweak parameters.

```bash
jupyter notebook notebook.ipynb
```

### Terminal Script

The script in `src/` lets you generate any of the four Bell states, simulate them, and automatically save the circuit and state measurements to the `images/` folder.

```bash
python src/bell_states.py --state phi_plus
```

Available arguments (adjust according to your actual implementation):

| Argument | Description | Possible values |
|---|---|---|
| `--state` | Bell state to generate | `phi_plus`, `phi_minus`, `psi_plus`, `psi_minus`, `all` |
| `--shots` | Number of simulation repetitions | Integer (default: 1024) |
| `--save` | Saves the generated images to `images/` | Flag (enabled by default) |

Example for generating all four states at once:

```bash
python src/bell_states.py --state phi+ --shots 2048 --save
```

> **Note:** check `src/bell_states.py` and update this argument table if your script uses different names or values.

## Generated Images

Each run saves two types of figures per state to the `images/` folder:

- **`circuits`**: diagram of the quantum circuit (H, CNOT, X, Z gates depending on the state) used to prepare the corresponding Bell state.
- **`measurements`**: visualization of the resulting quantum state, including the Bloch sphere, density matrix, and/or measurement histogram.

## Example Results

Generating the `Φ⁺` state produces:

- The circuit: a Hadamard gate on qubit 0 followed by a CNOT gate (control: qubit 0, target: qubit 1).
- When measured in the computational basis, only the outcomes `00` and `11` are observed, each with a probability of approximately 50%, demonstrating the perfect correlation between both qubits characteristic of entanglement.

## Contributing

Contributions are welcome. To propose changes:

1. Fork the repository.
2. Create a branch for your feature (`git checkout -b feature/new-feature`).
3. Make your changes and commit them (`git commit -m 'Add new feature'`).
4. Push the branch (`git push origin feature/new-feature`).
5. Open a Pull Request.

## License

This project is distributed under the [MIT](./LICENSE) license. Adjust this section if your project uses a different license.