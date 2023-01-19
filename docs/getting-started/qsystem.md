---
layout: page
menubar: docs_menu
title: Program Target Evolution
subtitle: Program your first quantum system
show_sidebar: false
toc: true
---

We start with programming an Ising model on a 3 qubit chain.

## Prepare the python environment

Run Python where Python path equals to the SimuQ folder.
```python
from simuq.qsystem import QSystem
from simuq.environment import qubit
```

## Define the evolution

First we create a quantum system and a list of qubits.
```python
qs = QSystem()
q = [qubit(qs) for i in range(n)]
```

Then we calculate the Ising Hamiltonian $$H=X_1X_2+X_2X_3+Z_1+Z_2+Z_3$$.
```python
h = q[0].X * q[1].X + q[1].X * q[2].X + q[0].Z + q[1].Z + q[2].Z
```

We add a $$T=1$$ time evolution under $$H$$ to the quantum system.
```python
T = 1
qs.add_evolution(h, T)
```
