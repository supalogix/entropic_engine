# Entropic Engine: A Finite State Physics Simulator

An experimental, open source project that simulates physics on a manifold using agent-based, energy-driven finite state automata. This simulator replaces conventional methods with a Turing machine–style approach.

Inspired by alternative approaches to conventional physics, our project draws motivation from ideas like Stephen Wolfram’s proposal that the universe can be described as a sufficiently complex cellular automaton. In this view, there exists a maximum speed—one cell per iteration—with objects changing form or vanishing and challenging traditional conservation laws. This unconventional perspective inspires our simulation framework, where **everything is energy**.

---

## Overview

The goal of this project is to build a simulation framework where:
- **Initial Conditions & Rules**: You set up the initial energy configurations and rules.
- **Emergent Dynamics**: The system evolves naturally, with state transitions representing shifts in energy distribution.
- **Realistic Physics**: The underlying mechanics are aligned with modern quantum mechanics and general relativity, modeling even subtle effects such as time dilation and gravitational potential—all without an explicit time variable.

In our model, the entire universe is reduced to energy interactions:
- **Massless Particles & the Higgs Field**: The simulation starts with massless particles carrying momentum. When these particles interact with a simulated Higgs field, energy becomes "trapped," forming localized energy packets that effectively have mass.
- **Curvature & Gravity**: These localized energy states influence the curvature of the manifold through an analogue of the energy–stress tensor, in line with Einstein’s field equations. In effect, energy tells the simulated spacetime how to curve, and the curved state space determines the "paths" (or state transitions) taken by the system.
- **Emergent Time**: There is no external clock. Instead, time emerges as the natural result of energy-driven state transitions. When energy is confined (as in a particle at rest), its only option is to "move" through time.

---

## Theoretical Foundations

One proposal, originally suggested by Stephen Wolfram, envisions physics as emerging from a sufficiently complex cellular automaton. In this model, each iteration represents a fundamental tick of time, and movement is naturally capped at one cell per iteration. While this inherently sets a maximum speed, it also implies that the traditional concept of an "object" becomes fuzzy—cells that can morph, merge, or vanish over time, making it challenging to directly apply conventional conservation laws.

To address this issue, we turn to Noether’s theorem, which establishes that conservation laws in inertial frames are a direct consequence of the underlying symmetries in the Lagrangian formulation of a system. The key idea is that if a system’s Lagrangian remains invariant under certain continuous transformations (such as time or space translations), then a corresponding quantity (like energy or momentum) is conserved.

Our approach attempts to reconcile these two viewpoints by treating each cell in the automaton as if it were its own inertial reference frame. By doing so, we aim to apply Noether’s theorem on a granular scale. This framework suggests that even though objects might not be well-defined in the conventional sense within a cellular automaton, the fundamental symmetries—and hence the conservation laws—can still manifest at the cellular level.

---

## Turing Machine-Based Simulation of a Solar System

We model solar system dynamics by representing celestial bodies as Turing machines interacting on a shared tape—encoding where orbital parameters and gravitational interactions are modeled as state transitions rather than explicit force calculations.
 
Although our current focus is on the solar system, our approach can be generalized to broader astrophysical scenarios in the future.

Each celestial body follows these principles:

### 1. Defining Celestial Bodies as Turing Machines

 - Each body maintains a state with position, momentum, total energy, and a vector clock to track causal consistency.

 - Motion is governed by energy conservation and Hamiltonian constraints.

### 2. Using the Shared Tape to Simulate Gravity

 - The Sun writes gravitational potential data, which planets read to determine acceleration.

 - Planets adjust kinetic and potential energy to ensure conservation, producing natural orbits.

### 3. Orbital Motion Without Explicit Time

 - Instead of discrete time steps, planets check for valid gravitational interactions before updating states.

 - Each body processes updates only when causally consistent based on light-speed constraints.

### 4. Multi-Body Interactions

 - Planets read gravitational influence from others, leading to emergent orbital perturbations.

 - Close encounters result in natural momentum exchanges, preserving angular momentum.

### 5. Incorporating Relativistic Effects

 - Light-speed delays ensure gravitational influence propagates at finite speed.

 - Time dilation emerges naturally as fast-moving bodies experience fewer state transitions.
---

## Proving the Correctness of Entropic Engine
Imagine our simulation as a feature film about a Turing machine. We ensure its accuracy by rigorously verifying our Turing machine’s behavior using formal methods. In this process, we rely on three key concepts that work together:

- **Theorem Prover (Coq)**: Coq is a theorem prover that mathematically checks the internal logic of our simulation. It proves that every step of the Turing machine’s operation follows from a set of rules. Think of it as a script editor who carefully reviews every line of a screenplay to ensure that every plot detail is logically sound.

- **Formal Specification Language (TLA+)**: TLA+ is a formal specification language that lets us describe the system’s behavior, including all its state transitions and invariants, in a precise mathematical way. It is similar to a detailed storyboard that lays out each scene in a film, ensuring that every transition from one state to the next is consistent and follows the intended plan.

- **Modal Logic (NuSVM 2)**: NuSVM 2 uses modal logic to verify the temporal aspects of our simulation. Modal logic extends classical logic to reason about time, possibility, and necessity. Imagine this tool as the film’s timekeeper and editor, ensuring that the timing, pacing, and sequence of events maintain a coherent and accurate flow over the entire runtime.

Together these tools form a comprehensive verification framework. The theorem prover (Coq) confirms that the internal logic is sound. The formal specification language (TLA+) provides a clear blueprint of the system’s state transitions. Modal logic (NuSVM 2) guarantees that the behavior over time remains consistent. By combining these methods, we rigorously ensure that our simulation accurately reflects the intended behavior of our Turing machine.

---

## Least Action-Based Turing Machine with Rebound

We are using **Rebound** to simulate a least action-based Turing machine:
 * The shared tape is replaced by state updates based on worldline interaction.
 * Each machine computes possible futures and selects the optimal path.
 * Hamiltonian constraints are respected by using Lagrangian formalism.

This approach ensures that the system evolves in a way that naturally obeys the principles of least action, with state transitions determined by energy distributions and interactions over worldlines.

---

## Why Use C Instead of Python?

We choose **C with Rebound** instead of Python for the following reasons:

- **True Parallelism**: Unlike Python, which relies on the Global Interpreter Lock (GIL), C offers true parallelism via OpenMP, MPI, and CUDA for high-performance simulations.
- **Performance Optimization with Assembly**: C allows us to optimize performance bottlenecks using inline assembly, separate assembly files, or SIMD (AVX, SSE) instructions. We took inspiration from the **DeepSeek** team, who demonstrated advanced techniques for optimizing with assembly, allowing us to further improve computational efficiency.
- **Memory Efficiency**: C provides fine-grained control over memory allocation (e.g., `malloc/free`) and ensures minimal overhead, crucial for large-scale simulations.

### Identifying Computation Bottlenecks in Rebound

To maximize performance, we optimize the following areas:

1. **Physics Calculations**: Optimize force updates, gravity computations, and collision detection.
2. **Vector Math & Matrix Transformations**: Enhance performance in rotation, scaling, and translation operations.
3. **Memory-Intensive Operations**: Improve batch processing, fast memory copies, and large dataset handling.
4. **Loop Optimizations**: Utilize SIMD vectorization to accelerate bulk computations.

### Using Inline Assembly for Small Optimizations

For targeted performance improvements, we integrate inline assembly into critical functions, leveraging:
- **SSE/AVX for vectorized arithmetic**
- **Hand-tuned assembly routines for memory management**
- **Fast lookup tables for computationally expensive operations**

---

## Related Research

Before developing this project, a review of existing computational models for simulating general relativity and the Einstein Field Equations was conducted. The following methods have been explored in the literature:

**Numerical Methods**

 - Introduction to Numerical Relativity (https://arxiv.org/pdf/2008.12931)
 - Numerical Relativity as a New Tool for Fundamental Cosmology (https://arxiv.org/pdf/2201.03752)
 - Evolution of Binary Black Hole Spacetimes (https://arxiv.org/pdf/gr-qc/0507014)
 - Numerical Relativity with Arbitrary Precision Arithmetic: Applications to Gravitational Collapse (https://arxiv.org/pdf/1803.00858)
 - Part III Gravitational Waves and Numerical Relativity(https://www.damtp.cam.ac.uk/user/us248/Lectures/Notes/gwnr.pdf)

**Finite Element Methods (FEM)**

- Finite Element Methods for the Einstein Field Equations. (https://arxiv.org/pdf/2310.18802)
- A New Approach to Finite Element Simulations of General Relativity(https://www-users.cse.umn.edu/~arnold/papers/QuennevilleThesis.pdf)
- Binary black hole simulation with an adaptive finite element method II: Application
of local discontinuous Galerkin method to Einstein equations (https://arxiv.org/pdf/1805.10640)
- A New Approach to Finite Element Simulations of
General Relativity (https://conservancy.umn.edu/server/api/core/bitstreams/3e4f1370-dc55-4690-83d5-017c7a48380e/content)
- Generating Initial Data in General Relativity using
Adaptive Finite Element Methods (https://arxiv.org/pdf/0801.3142)

**Cellular Automata**

 - A New Kind of Science. (https://www.amazon.com/New-Kind-Science-Stephen-Wolfram/dp/1579550088)
 - CELLULAR AUTOMATA THEORY AND PHYSICS (https://arxiv.org/pdf/physics/9907013)
 - Photonic cellular automaton simulation of relativistic quantum fields: Observation of Zitterbewegung (https://journals.aps.org/prresearch/pdf/10.1103/PhysRevResearch.6.033136)
 - SPECIAL RELATIVITY DERIVED FROM CELLULAR AUTOMATA THEORY: The origin of the universal speed limit (https://arxiv.org/pdf/physics/9902034)
 - Doubly-Special Relativity from Quantum Cellular Automata (https://arxiv.org/pdf/1310.6760)
 - Exploring Rulial Space: The Case of Turing Machines (https://arxiv.org/pdf/2101.10907)
 - The Problem of Distributed Consensus: A Survey (https://arxiv.org/pdf/2106.13591)

**Symbolic Computation**

 - Finite element approximation of the Einstein tensor (https://arxiv.org/pdf/1703.09738)
 - Computational General Relativity in the Wolfram Language using Gravitas I: Symbolic and Analytic Computation (https://arxiv.org/pdf/2308.07508)
 - Symbolic Computation of Dynamics on Smooth Manifolds (https://hybrid-robotics.berkeley.edu/publications/WAFR2016_SymDynamics_Manifolds.pdf)
 - Symbolic tensor calculus on manifolds: a SageMath implementation (https://arxiv.org/pdf/1804.07346)
 - Symbolic Calculus for Value Boundary Problems on Manifolds and Edges (https://d-nb.info/1218377879/34) 

None of these approaches use a fully energy-driven, finite state automaton model similar to Entropic Engine.

---

## Acknowledgements

- **The Rebound Project**: A special thanks to the Rebound team for their incredible effort in developing and maintaining an efficient N-body simulation framework, which forms a crucial part of our work (https://rebound.readthedocs.io/en/latest/).
- **DeepSeek**: For their invaluable insights into assembly optimization, helping us refine our approach to performance improvements in C (https://github.com/deepseek-ai).
- **Stephen Wolfram** and his book **A New Kind of Science**: His work on cellular automata and computational approaches to physics has been a major inspiration for this project.
- **Matt Strassler** and his website [profmattstrassler.com](https://profmattstrassler.com/) for his notion of "rate of flipping" as a mechanical effect rather than a mysterious field property. His analogy of a perpetual light in a mirrored box helped shape our understanding of how the rate of flipping relates to mass and acceleration effects. While this analogy has its limitations, it provides an intuitive way to think about how repeated interactions can lead to mass-like behavior in a confined system.


---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

MIT License

Copyright (c) 2025 Jonathan Nacionales

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

---

*Happy simulating!*

