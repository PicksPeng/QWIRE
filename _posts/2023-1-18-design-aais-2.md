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

Superconducting circuits are a promising platform for scalable quantum computing. Carefully constructed mesoscopic circuits can be designed to have quantum behavior, allowing easier exploitation of quantum effects for quantum computation. A superconducting LC oscillator can be quantized in terms of the phase and charge moving within the circuit, and by replacing the inductor with a Josephson Junction, a component serving as a nonlinear inductor, the oscillator becomes anharmonic, separating out the lower two energy levels of the oscillation to use as the computational basis of a qubit. Treating each oscillator as a two-level system yields the approximate qubit Hamiltonian $$H = \omega_z \frac{\sigma_z}{2}$$
