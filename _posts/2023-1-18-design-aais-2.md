---
layout: post
title:  "Tutorial: design an AAIS (II)"
date:   2023-01-14 12:00:00
categories: tutorial
description: "The design of an AAIS for IBM's transmon qubit machines"
image: 'https://media.nature.com/lw767/magazine-assets/d41586-021-03476-5/d41586-021-03476-5_19875844.jpg?as=webp'
published: true
author: Jacob Young
---

We introduce the design ideas of an AAIS from the viewpoint of a device provider. In this tutorial, we briefly discuss superconducting machines with fixed-frequency transmon qubits and present how to build an AAIS based on these machines.


## Superconducting Qubits

Superconducting circuits are a promising platform for scalable quantum computing. Carefully constructed mesoscopic circuits can be designed to have quantum behavior, allowing easier exploitation of quantum effects for quantum computation. A simple superconducting LC oscillator can be quantized in terms of the phase and charge moving within the circuit, and by replacing the inductor with a Josephson Junction, a component serving as a nonlinear inductor, the oscillator becomes anharmonic, separating out the lower two energy levels of the oscillation to use as the computational basis of a qubit. Treating each oscillator as a two-level system yields the approximate qubit Hamiltonian $$H = \omega_q \frac{\sigma_z}{2}$$, where $$\omega_q$$ is the oscillation frequency of the qubit's precession about the z-axis. When constructed with certain circuit parameters, this simple anharmonic oscillator is known as a transmon qubit.

## Superconducting Qubit Control

Qubit control is accomplished through the use of signal lines, dedicated signal paths where arbitrary waveform generators can modify the Hamiltonian of the qubit(s) affected by that line. For a single qubit drive line, in the frame of reference rotating with the qubit, the qubit has no system Hamiltonian, and the Hamiltonian induced by a pulse applied to the drive line may be written as $$H_d = g_d s(t) (I \sigma_x + Q \sigma_y)$$, where $$g_d$$ and $$s(t)$$ are the interaction strength and signal envelope for the applied pulse and $$I$$ and $$Q$$ are the in-phase and out-of-phase components of the pulse, respectively. We emphasize that to produce this Hamiltonian in the rotating frame, in the lab frame, pulses are constructed with a frequency matching the qubit's.

This format for single-qubit drive operations gives rise to an important feature of superconducting qubits- the free Z rotation. The phase of the drive signal relative to the qubit determines whether an X or Y rotation is performed- the same thing accomplished by rotating a qubit about its Z axis. Furthermore, because measurements are performed in the Z basis, the global phase of a given qubit is irrelevant. Updating the phase used when sending drive signals to the qubit is equivalent to performing a single-qubit Z rotation. Tracking this phase shift in software instead of driving the qubit allows for instantaneous, parametrized, error-free Z rotations.

For multi-qubit entangling lines, two coupled fixed-frequency transmon qubits are entangled through the cross-resonance interaction. This interaction is induced by driving one qubit at the other qubit's frequency, resulting in a Hamiltonian of the form $$H_{CR} = g_{CR} s(t) (\nu \sigma_x \otimes I + \mu I \otimes \sigma_x + \sigma_z \otimes \sigma_x)$$, where $$g_{CR}$$, $$\nu$$, and $$\mu$$ are interaction strength constants, $$s(t)$$ is the signal envelope, and the tensor product indicates Hamiltonian terms affecting both systems. A ZX polyrotation may be extracted from this Hamiltonian through the careful application of multiple drive signals on both qubits, resulting in an effective Hamiltonian of $$H_{eff} = g_{CR} \sigma_z \otimes \sigma_x$$.
