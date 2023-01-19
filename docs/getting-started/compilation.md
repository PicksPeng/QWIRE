---
layout: page
menubar: docs_menu
title: Compile to Qiskit Pulse Schedules
subtitle: Compile your target evolution to IBM Qiskit pulse schedules
show_sidebar: false
toc: true
---

Assume that we have `qs` as the target system to simulate, and we want to compile it to an IBM machine (`ibmq_jakarta` in this case).

## Import the machine object

We first import the IBM machine object from the `FakeJakarta` machine backend.

```python
from qiskit.providers.fake_provider import FakeJakarta
from aais.ibm import get_mach
mach = get_mach(FakeJakarta())
```

## Synthesize an abstract schedule

We then apply the SimuQ solver to solve and store the intermediate representation into an file.

```python
from simuq.solver import generate_as
as = generate_as(qs, mach)
with open("qs.as","w+") as f:
    f.write(str(as[1])+"\n")
    for item in as[2] + as[3]:
        f.write(str(item)+"\n")
```

## Generate pulse schedule

We then apply a scheduler to generate a concrete schedule and a transpiler to generate the final pulse schedule.

```python
from backends.Analog_Hamiltonian_Simulation.Analog_Hamiltonian_Simulator.IBM_Machine_new import IBM_Machine
from backends.Analog_Hamiltonian_Simulation.Analog_Hamiltonian_Simulator.Program import Program

program = Program(IBM_Machine(FakeJakarta()))
program.init_from_file("qaoa.as")

program.schedule()
program.transpile()
program.pulse_schedule.generate_external_schedule()
```

One can view the pulse schedule by `program.pulse_schedule.draw()`.