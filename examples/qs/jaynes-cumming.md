---
title: Jaynes-Cumming model
subtitle: Programming Jaynes-Cumming model in HML
layout: default
show_sidebar: false
---

The Jaynes–Cummings model (sometimes abbreviated JCM) is a theoretical model in quantum optics. It describes the system of a two-level atom interacting with a quantized mode of an optical cavity (or a bosonic field), with or without the presence of light (in the form of a bath of electromagnetic radiation that can cause spontaneous emission and absorption). 

The Hamiltonian of a Jaynes–Cummings model with one qubits can be described as 
$$\hat{H}_{\mathrm{JC}}=\hbar \omega_c \hat{a}^{\dagger} \hat{a}+\hbar \omega_a \frac{\hat{\sigma}_z}{2}+\frac{\hbar \Omega}{2}\left(\hat{a} \hat{\sigma}_{+}+\hat{a}^{\dagger} \hat{\sigma}_{-}\right)$$
where $$\omega_c, \omega_a$$ and $$\Omega$$ are real-valued coupling constants. This Hamiltonian can be described by the following HML code:

```python
import numpy as np
from simuq.environment import qubit
from simuq.qsystem import QSystem


def Hensenberg_model(n_qubits, omega_c, omega_a, Omega, T):
    qs = QSystem()
    ql = [qubit(qs) for i in range(n_qubits)]
    ham = 0
    ham -= Jx * ql[q0].X * ql[q1].X / 2
    ham -= Jy * ql[q0].Y * ql[q1].Y / 2
    ham -= Jz * ql[q0].Z * ql[q1].Z / 2
    qs.add_evolution(ham, T)
    return qs
```