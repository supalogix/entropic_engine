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

One proposal, originally suggested by Stephen Wolfram, envisions physics as emerging from a sufficiently complex cellular automaton. In this model, each iteration represents a fundamental tick of time, and movement is naturally capped at one cell per iteration. While this inherently sets a maximum speed, it also implies that the traditional concept of an "object" becomes fuzzy (i.e. cells that can morph, merge, or vanish over time) which makes it challenging to directly apply conventional conservation laws.

In the context of Stephen Wolfram's theory, which suggests that physical phenomena can be modeled using cellular automata, the idea of objects changing form or vanishing refers to the nature of entities in a discrete, grid-like universe.

- **Changing Form**: This implies that the properties or states of objects can evolve based on the rules of the cellular automaton. For example, an object might rearrange its structure, change its color, or alter its position based on interactions with neighboring cells or following specific rules. This dynamic nature means that what defines an object can be fluid, as it can take on different appearances or behaviors over time.

- **Vanishing**: This suggests that objects can cease to exist within the system, potentially due to the rules of the automaton leading to their destruction or transformation into energy or other states. In a cellular automaton, the local rules can lead to situations where a configuration of cells that represents an object might evolve into a state that no longer has the same structure or properties, effectively making that object "vanish."

In this framework, the concept of an "object" becomes less rigid, as it is defined by its current state and the rules governing its interactions rather than by inherent properties. This fluidity challenges traditional notions of conservation laws, which rely on the stability and continuity of objects in space and time. If objects can transform or disappear, it becomes difficult to maintain fixed conservation principles, such as conservation of mass or energy, in the same way we understand them in classical physics.

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/e/e5/Gospers_glider_gun.gif" alt="Animated GIF">
</p>

To address this issue, we turn to Noether’s theorem, which establishes that conservation laws in inertial frames are a direct consequence of the underlying symmetries in the Lagrangian formulation of a system. The key idea is that if a system’s Lagrangian remains invariant under certain continuous transformations (such as time or space translations), then a corresponding quantity (like energy or momentum) is conserved.

Our approach attempts to reconcile these two viewpoints by treating each cell in the automaton as if it were its own inertial reference frame. By doing so, we aim to apply Noether’s theorem on a granular scale. This framework suggests that even though objects might not be well-defined in the conventional sense within a cellular automaton, the fundamental symmetries—and hence the conservation laws—can still manifest at the cellular level.

This dynamic view of energy distribution resonates with a broader historical evolution in our understanding of time and space. To Newton, time was simply a parameter, a fixed backdrop against which events unfolded; space was similarly unchanging. Einstein, however, brought these dimensions to life: time and space dance with mass and energy and form a fabric that is intrinsically linked to the physical processes of the universe. By analogy, our approach to the cellular automaton is to treat each cell as if it were its own inertial reference frame. Here, mass-energy is initially treated as a fixed parameter (i.e. a constant element within each cell) but it is brought to life through what Dr. Matt Strassler calls the "rate of flipping." As an analogy, think of a perpetual light bouncing inside a mirrored box. This shapes our understanding of how the rate at which cells “flip” can give rise to mechanical effects such as mass and acceleration. In essence, mass is just the energy trapped in a mirrored box, ready to be redistributed.

In our unified view of emergent physics, the universe is modeled as a vast cellular automaton: a grid of immutable cells that never change their inherent form. What appears as change is, in fact, the dynamic redistribution of energy among these cells.

In Stephen Wolfram’s vision, the grid evolves so that objects seem to change form or even vanish as cells interact. However, the deeper truth is that the cells themselves remain constant; they only appear to transform because the energy within them shifts according to fixed rules. This energy transfer, governed by the second law of thermodynamics, is what gives rise to the fluid behavior of observable phenomena.

Similarly, an object’s apparent disappearance is not due to the cell ceasing to exist. Instead, visibility is an emergent property: an object is visible only when a cell contains energy in the appropriate configuration. When a cell seems to “lose” an object, it is merely in a low-energy state that fails to manifest that object. The cell remains, faithfully obeying conservation laws, while the energy rearrangement creates the illusion of vanishing.

Thus, by synthesizing these perspectives, we resolve the apparent paradox: the cellular automaton’s fundamental rules ensure that energy is conserved at every level.

---

## Turing Machine-Based Simulation of a Solar System

We model solar system dynamics by representing celestial bodies as Turing machines interacting on a shared tape—encoding where orbital parameters and gravitational interactions are modeled as state transitions rather than explicit force calculations.
 
Although our current focus is on the solar system, our approach can be generalized to broader astrophysical scenarios in the future.

Each celestial body follows these principles:

1. **Defining Celestial Bodies as Turing Machines**
   - Each body maintains a state with position, momentum, total energy, and a vector clock to track causal consistency.
   - Motion is governed by energy conservation and Hamiltonian constraints.

2. **Using the Shared Tape to Simulate Gravity**
   - The Sun writes gravitational potential data, which planets read to determine acceleration.
   - Planets adjust kinetic and potential energy to ensure conservation, producing natural orbits.

3. **Orbital Motion Without Explicit Time**
   - Instead of discrete time steps, planets check for valid gravitational interactions before updating states.
   - Each body processes updates only when causally consistent based on light-speed constraints.

4. **Multi-Body Interactions**
   - Planets read gravitational influence from others, leading to emergent orbital perturbations.
   - Close encounters result in natural momentum exchanges, preserving angular momentum.

5. **Incorporating Relativistic Effects**
   - Light-speed delays ensure gravitational influence propagates at finite speed.
   - Time dilation emerges naturally as fast-moving bodies experience fewer state transitions.

---

## Modeling Approach Overview

A modeling approach is crucial for understanding behavior because it transforms complex system dynamics into a clear, structured blueprint that makes it much easier to predict and analyze each step.

We use the following:

- **2‑State, 2‑Color Turing Machines**:  Like a minimalist recipe using just two ingredients that still creates a gourmet dish,
they show how minimal components can lead to universal and unpredictable computation.
- **Petri Nets**: Imagine a city map where tokens (cars) navigate intersections (transitions) across streets (places). These provide a clear, visual picture of state changes and concurrent processes.
- **Lambda Calculus**: Think of it as a script editor refining each line of a screenplay to ensure the story unfolds flawlessly:
It abstracts computations into elegant, symbolic reductions that help verify correctness step by step.

Together, these tools offer a rich, multi-perspective toolkit for modeling and analyzing the behavior of our Turing machine.

---

## Proving the Correctness of Entropic Engine
Imagine our simulation as a feature film about a Turing machine. We ensure its accuracy by rigorously verifying our Turing machine’s behavior using formal methods. In this process, we rely on three key concepts that work together:

- **Theorem Prover (Coq)**: Coq is a theorem prover that mathematically checks the internal logic of our simulation. It proves that every step of the Turing machine’s operation follows from a set of rules. Think of it as a script editor who carefully reviews every line of a screenplay to ensure that every plot detail is logically sound.

- **Formal Specification Language (TLA+)**: TLA+ is a formal specification language that lets us describe the system’s behavior, including all its state transitions and invariants, in a precise mathematical way. It is similar to a detailed storyboard that lays out each scene in a film, ensuring that every transition from one state to the next is consistent and follows the intended plan.

- **Modal Logic (NuSVM 2)**: NuSVM 2 uses modal logic to verify the temporal aspects of our simulation. Modal logic extends classical logic to reason about time, possibility, and necessity. Imagine this tool as the film’s timekeeper and editor, ensuring that the timing, pacing, and sequence of events maintain a coherent and accurate flow over the entire runtime.

Together these tools form a comprehensive verification framework. 
- The theorem prover (Coq) confirms that the internal logic is sound. 
- The formal specification language (TLA+) provides a clear blueprint of the system’s state transitions. 
- Modal logic (NuSVM 2) guarantees that the behavior over time remains consistent. 

By combining these methods, we rigorously ensure that our Turing Machine accurately reflects the intended physics behavior.

---

## Least Action-Based Turing Machine with Rebound and Energy–Spacetime Dynamics

We are using **Rebound** to simulate a Turing machine whose state transitions are determined not by an explicit “tape” but by energy configurations and worldline interactions. In this framework, every computational element evolves by selecting its optimal future based on Hamiltonian constraints, ensured through Lagrangian formalism, and more fundamentally through the conservation and transformation of energy.

### Energy as the Basis for Computation

Rather than directly stating “this takes X time,” our system relies on the fact that energy is the sole currency of dynamics. In physics, the evolution of a system is governed by the principle of least action, meaning that the energy distribution (and its subsequent shifts) defines both spatial and temporal behavior. For example:

- **Energy Localization and Rest Mass:**  The concept is analogous to energy being "trapped" between mirrors. This confined energy, representing what we call potential energy, becomes the particle’s rest energy. In the special case of massive particles, this is given by  `E = m c^2`  However, the complete energy–momentum relation is  `E^2 = (m c^2)^2 + (p c)^2`,  where for massless particles (with m = 0), the energy is simply  `E = p c`.  Even when the energy is confined, it must propagate, if not in space then along the time axis. In an inertial frame (one in which an object either remains at rest or moves at a constant velocity unless acted upon), this propagation is natural because an object at rest (relative to that frame) still has momentum if it is moving through time.

- **Momentum in an Inertial Frame:**  Momentum is defined as  `p = m v`.  Even though the energy is localized within the "mirrors" (i.e., a confined region), its inevitable propagation along the time axis is equivalent to the object moving at the speed of light in time. This is why, in any inertial frame, a particle’s four-velocity is given by  `u^mu = (c, 0, 0, 0)`,  ensuring that the particle’s rest energy  `E = m c^2`  (and more generally the full energy `E^2 = (m c^2)^2 + (p c)^2`) contributes consistently to the stress-energy tensor that curves spacetime:  `G_munu = (8*pi*G)/(c^4) * T_munu`, where `T_munu = rho * u_mu * u_nu`.

- **Conversion of Energy Forms:**  Just as gravitational potential energy converts into kinetic energy (via  `PE = mgh`  and  `KE = 1/2 * m * v^2`),  the "rate of flipping" or the zigzagging of energy within its confined space not only defines the particle’s inertial properties but also how it navigates through spacetime. The more rapid this intrinsic motion (or "flip"), the more localized the energy appears, a classical intuition behind the wave/particle duality.

### Time Emergence from Energy Dynamics

Because energy is the only fundamental entity we manipulate, "time" emerges from the patterns of energy movement. A particle at rest in space still "moves" through time because the trapped energy is forced along the only available dimension.

- The **Lagrangian principle** dictates that every system follows the path of least resistance; in our case the geodesic that maximizes proper time.
- With no spatial direction available (for a particle at rest), the energy’s propagation is directed solely upward through time. Think of it as a perpetual light in a mirrored box: it must travel somewhere, so if spatial propagation is blocked, it continues along the time axis.

### Numerical Simulation with Rebound and Symplectic Integration

Rebound, while originally built for Newtonian N-body simulations, offers a robust platform for calculating complex dynamical systems using [symplectic integrators](https://rebound.readthedocs.io/en/latest/integrators/). These integrators preserve the underlying Hamiltonian structure and are ideal for long-term simulations where conservation of energy is paramount. 



Our implementation leverages Rebound to:

- **Compute Geodesics:**  By using a symplectic integrator, we can numerically compute the geodesic—the path of least action—that each automaton (or computational element) must follow in order to conserve energy.

- **Simulate Energy–State Transitions:**  Each automaton "computes" its possible futures based solely on how its energy is arranged and redistributed, without self-referential timing. This ensures that time dilation and message delay emerge naturally from the energy interactions rather than being arbitrarily imposed.

- **Maintain Conservation Laws:**  Since every automaton follows the same physical rules (derived from the energy-stress tensor and Lagrangian formalism), the overall system guarantees energy conservation from all perspectives. Rebound's integrators make it feasible to perform these Hamiltonian and Lagrangian calculations in a specific inertial frame using optimized numerical methods.

### Bridging Computation and Fundamental Physics

In essence, our approach transforms the classical ideas of potential and kinetic energy, inertial frames, and geodesic motion into a computational paradigm. The state transitions of our Turing machine are dictated by:

- **Energy Confinement and Release:**  In the same way that a falling mass converts potential energy to kinetic energy, our system uses energy redistribution to signal state changes.

- **Natural Time Evolution:**  Even if energy is confined spatially (as in a mirrored box), it must propagate in time, providing a natural "tick" for the computational process.

- **Optimal Path Selection:**  Following the principle of least action, each automaton selects the path (or state update) that minimizes the action, mirroring how particles in a gravitational field follow geodesics.

By grounding our simulation in these principles, we avoid the need for explicit time delays (which would be self-referential and problematic in a Turing/Godel framework) and instead allow time to emerge from the fundamental interactions of energy in spacetime.

Leveraging tools like Rebound and its symplectic integrators provides a practical headstart even when extending them beyond their originally intended purpose.

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
- **Dr. Don V. Black** for his patient guidance.


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

