---
title: SimuQ
subtitle: A domain-specific language for quantum simulation with analog compilation
layout: page
callouts: home_callouts
show_sidebar: false
---

SimuQ is a domain-specific language designed for quantum simulation problem on near-term quantum devices. SimuQ aims to reduce domain barriers in simulating Hamiltonian evolution on real quantum devices for users with minimal physics knowledge. We provide an open-source Python implementation of SimuQ, and a solver-based compilation framework generating pulse-level control code for multiple platforms of quantum devices include IBM's Qiskit Pulse for superconducting transmon qubit devices, QuEra's Bloqade for neutral atom arrays, and quantum circuits for other general machines.

<a href="https://github.com/PicksPeng/SimuQ" class="btn">View on GitHub</a>
<a href="https://github.com/PicksPeng/SimuQ/archive/refs/heads/main.zip" class="btn">Download .zip</a>

# Installation

Download SimuQ from GitHub or above link.

We have tested our implementation with `Python 3.9` and the following packages:
* `NetworkX 2.8.7`
* `NumPy 1.23.4`
* `SciPy 1.9.3`

To generate quantum circuits in Qiskit, IBM machine AAIS for specific machines, or programs in Qiskit Pulses, the following packages are also required:
* `Qiskit 0.39.0`
* `Qiskit-Terra 0.22.0`

The generated Bloqade programs are tested in `Julia 1.7.2` with `Bloqade 0.1.13`.

# Documentation

For full instructions, please see the [Documentation](/QWIRE/docs/)

# Citations

If you are using SimuQ in your work, please cite:
```
@article{peng2023simuq,
  title         = {SimuQ: A Domain-Specific Language for Quantum Simulation with Analog Compilation}
  author        = {Peng, Yuxiang and Young, Jacob and Liu, Pengyu and Wu, Xiaodi},
  year          = {2023},
  month         = jan,
}
```

# Acknowledgements

This project was partially funded by the U.S. Department of Energy, Office of Science, Office of Advanced Scientific Computing Research, Quantum Testbed Pathfinder Program under Award Number DE-SC0019040, Air Force Office of Scientific Research under award number FA9550-21-1-0209, and  the U.S. National Science Foundation grant CCF-1942837 (CAREER).