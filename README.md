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

### Stephen Wolfram’s Cellular Automaton Model  
Stephen Wolfram suggests that physics could emerge from a **complex cellular automaton**, where each iteration represents a fundamental tick of time. In this setup, movement is naturally limited to one cell per iteration, meaning there’s a built-in speed limit. But the real challenge isn’t just speed—it’s that objects don’t stay fixed. They can **morph, merge, or vanish**, making it tricky to apply traditional conservation laws.  

### What Happens to Objects?  
In a **discrete, grid-like universe**, objects aren’t permanent. They change form, shift states, or disappear based on local rules:  
- **Changing Form**: Objects evolve as they interact with neighboring cells. They might rearrange, change properties, or transform based on predetermined rules.  
- **Vanishing**: Objects don’t truly disappear; instead, their configuration shifts. Energy may redistribute in a way that makes them unrecognizable, creating the illusion of destruction.  

Think of it like pixels on a screen. A shape might vanish, but the pixels are still there, just displaying something else.  

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/e/e5/Gospers_glider_gun.gif" alt="Animated GIF">
</p>  

### Noether’s Theorem & Conservation Laws  
Conservation laws, as we know them, rely on stable, continuous objects. But what if objects aren’t well-defined? **Noether’s theorem** tells us that conservation laws come from underlying symmetries. If a system behaves the same over time, energy is conserved. If it behaves the same across space, momentum is conserved.  

In our approach, instead of applying conservation laws to entire objects, we apply them **at the cellular level**. Each cell acts as its **own reference frame**, ensuring that even if objects shift or disappear, fundamental symmetries remain intact.  

### A New Perspective on Space, Time, and Energy  
- **Newton’s View**: Time is a passive backdrop, where things happen.  
- **Einstein’s View**: Time and space interact dynamically with mass and energy.  
- **Cellular Automaton View**: The cells don’t change, but the **energy inside them moves around**, creating the illusion of motion.  

This is where [rate of flipping](https://profmattstrassler.com/articles-and-posts/particle-physics-basics/the-known-apparently-elementary-particles/the-known-particles-if-the-higgs-field-were-zero/) comes in. Imagine light bouncing inside a mirrored box, and what we call mass might just be **trapped energy** that is constantly redistributing.  

### Resolving the Conservation Paradox  
Even though objects seem to appear and disappear, **energy is never lost**—it just shifts configurations. The second law of thermodynamics keeps everything in check, ensuring that what looks like randomness is actually governed by deeper principles.  

### Final Thoughts  
If we rethink physics as a cellular automaton, conservation laws don’t vanish. No, they just apply at a smaller, more fundamental scale. Objects may not be permanent, but the **rules governing their interactions remain unchanged**.  

For a deeper dive, check out:  
- **[Emergent Dynamics: A Kinematic-First Approach](./scientific_background/EMERGENT_DYNAMICS.md)**
---

## Turing Machine-Based Simulation of a Solar System with Voxelized Manifold Perspectives

We model solar system dynamics by representing worldlines as Turing machines interacting on a shared tape. In addition to modeling orbital parameters and gravitational interactions as state transitions, each Turing machine maintains a record of a discretized manifold.

This manifold is composed of voxels which is analogous to pixels in an image that represent a continuous smooth surface.

Each celestial body records its manifold from its own perspective, and these voxelized state space vectors can be used to cross verify that the perspectives of different worldlines are mutually compatible.

Furthermore, each Turing machine is modeled as being in its own independent inertial frame of reference. Because of this, the momentum is zero by definition. Technically, only when there is a collision of some kind is the momentum non-zero. This is when the worldline is not in an inertial reference frame. Once the system has equalized, the worldline will return to a state of being in an inertial frame of reference. Additionally, worldlines can appear and disappear through the processes of energy combining and decomposing. However, these dynamics are not accounted for in the current state of the system and may be introduced in the future. For the time being, we assume that there are no collisions within the system.

Given that the Lagrangian inherently encapsulates the dynamics from which momentum can be derived, it is more precise in this context to record the Lagrangian rather than the momentum directly.

Each celestial body follows these principles:

1. **Defining Celestial Bodies as Turing Machines**
   - Each body maintains a state with position, total energy, the Lagrangian (which inherently captures the gravitational and momentum information), and a vector clock to track causal consistency.
   - In addition, each Turing machine records a voxelized representation of the surrounding state space—a discretized manifold where each voxel carries vector data describing local curvature and metric information from that body's perspective.
   - Motion is governed by Lagrangian and Hamiltonian constraints.

2. **Agent-Based Simulation of Gravitational Interactions**
   - Gravitational influence is entirely decentralized: each Turing machine computes its local gravitational interactions based on the voxelized state data recorded by neighboring agents.
   - Each body independently evaluates the influence of other bodies by reading their local state vectors and adjusting its own state accordingly, ensuring conservation of energy.
   - The voxelized manifold provides a framework for each agent to map out gravitational effects, facilitating cross-verification of interactions across different perspectives.

3. **Orbital Motion Without Explicit Time**
   - Instead of discrete time steps, bodies check for valid gravitational interactions before updating states.
   - Each body processes updates only when causally consistent based on light-speed constraints.
   - The continuous manifold record enables bodies to reconcile their state transitions by comparing the voxel vector maps across worldlines.

4. **Multi-Body Interactions**
   - Bodies read gravitational influences from one another, leading to emergent orbital perturbations.
   - Close encounters result in natural momentum exchanges, preserving angular momentum.
   - Each Turing machine’s perspective of the manifold allows for cross verification: the relative voxel vectors help ensure that despite different local views, all bodies agree on the overarching causal structure of the simulated space.

5. **Incorporating Relativistic Effects**
   - Light-speed delays ensure gravitational influence propagates at finite speed.
   - Time dilation emerges naturally as fast-moving bodies experience fewer state transitions.
   - The voxelized manifold provides a flexible and localized method to capture relativistic effects by allowing each body to record and compare the curvature of spacetime as seen from its own reference frame.

---

## Least Action-Based Turing Machine with Rebound and Energy–Spacetime Dynamics  

We use [Rebound](https://rebound.readthedocs.io/en/latest/) to simulate a Turing machine where state transitions are governed by energy configurations and interactions along worldlines. Instead of predefined steps, each computational element **selects its optimal future** based on Hamiltonian constraints, guided by Lagrangian formalism and energy conservation. While energy and momentum are frame-dependent, the **underlying physical laws remain invariant** across different perspectives.  

---

## Energy as the Basis for Computation  

Our system treats **energy as the fundamental driver of computation**. The system evolves according to the **principle of least action**, meaning that the way energy distributes itself **determines both spatial and temporal behavior**. However, defining a Lagrangian in this framework is tricky because:  
- It **doesn’t rely on conventional spatial derivatives**.  
- Instead, it **requires a regression-based approach** to approximate changes in state.  

### Key Principles  

- **Energy Localization and Rest Frames**  
  - In an object’s **rest frame**, it has zero momentum and only **potential energy**.  
  - Each computational cell acts as **its own reference frame**, so energy must be analyzed locally rather than globally.  

- **Momentum and Frame Dependence**  
  - An object’s momentum depends on the observer’s motion.  
  - Noether’s theorem ensures that even though different observers assign different values to energy components, **the system’s total behavior remains consistent** across frames.  

- **Energy Confinement and Propagation**  
  - Energy can be thought of as **trapped between mirrors**, much like a particle’s **rest energy** (analogous to Einstein’s mass-energy relation).  
  - The challenge is ensuring that numerical methods **respect conservation laws** across all reference frames.  

---

## Time Emergence from Energy Dynamics  

Since energy is the **only fundamental quantity** we track, **time itself emerges** from patterns of energy movement. Even an object at rest **moves through time**, as its potential energy is still active along the time axis.  

- The **Lagrangian principle** ensures that every system follows the **path of least resistance**: in this case, the geodesic that maximizes proper time.  
- If an object **can’t move spatially**, its energy still propagates along the time axis, much like light bouncing in a mirrored box.  

### The Numerical Challenge  
- Traditional Lagrangian mechanics rely on smooth derivatives, but our system **operates in a discrete space**.  
- Instead of conventional differentiation, a **regression-based approach** is needed to dynamically infer the least-action path.  

---

## Numerical Simulation with Rebound and Symplectic Integration  

Rebound, originally designed for N-body simulations, is used to model complex **energy-driven systems** with symplectic integration.  
- **Why Symplectic Methods?**  
  - They preserve **conservation laws** and **numerical stability** over long simulations.  
  - Since our model doesn’t define forces explicitly, we rely on symplectic methods to **maintain energy consistency across state transitions**.  

### Why We Use Rebound  

- **Preserves Conservation Principles**  
  - Each computational element follows a trajectory dictated by **energy redistribution**, and symplectic integration ensures **total energy consistency** over time.  

- **Allows State Transitions Without an Imposed Clock**  
  - Time **emerges from energy flow**, and symplectic integration naturally aligns with this by **preserving system evolution without needing an external clock**.  

- **Maintains Numerical Integrity Across Reference Frames**  
  - Symplectic methods **preserve energy and angular momentum globally**, making them ideal for handling transformations between different inertial frames.  

By leveraging Rebound’s [symplectic integration](https://rebound.readthedocs.io/en/latest/integrators/), we ensure that **our system remains stable, energy-conserving, and dynamically emergent**, even without explicitly defining forces or a traditional time step.  

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

## Related Research

Before developing this project, a review of existing computational models for simulating general relativity and the Einstein Field Equations was conducted. The following methods have been explored in the literature:

**Numerical Methods**

 - [Introduction to Numerical Relativity](https://arxiv.org/pdf/2008.12931)
 - [Numerical Relativity as a New Tool for Fundamental Cosmology](https://arxiv.org/pdf/2201.03752)
 - [Evolution of Binary Black Hole Spacetimes](https://arxiv.org/pdf/gr-qc/0507014)
 - [Numerical Relativity with Arbitrary Precision Arithmetic: Applications to Gravitational Collapse](https://arxiv.org/pdf/1803.00858)
 - [Part III Gravitational Waves and Numerical Relativity](https://www.damtp.cam.ac.uk/user/us248/Lectures/Notes/gwnr.pdf)

**Finite Element Methods (FEM)**

- [Finite Element Methods for the Einstein Field Equations](https://arxiv.org/pdf/2310.18802)
- [A New Approach to Finite Element Simulations of General Relativity](https://www-users.cse.umn.edu/~arnold/papers/QuennevilleThesis.pdf)
- [Binary black hole simulation with an adaptive finite element method II: Application of local discontinuous Galerkin method to Einstein equations](https://arxiv.org/pdf/1805.10640)
- [A New Approach to Finite Element Simulations of General Relativity](https://conservancy.umn.edu/server/api/core/bitstreams/3e4f1370-dc55-4690-83d5-017c7a48380e/content)
- [Generating Initial Data in General Relativity using Adaptive Finite Element Methods](https://arxiv.org/pdf/0801.3142)

**Cellular Automata**

 - [CELLULAR AUTOMATA THEORY AND PHYSICS](https://arxiv.org/pdf/physics/9907013)
 - [Photonic cellular automaton simulation of relativistic quantum fields: Observation of Zitterbewegung](https://journals.aps.org/prresearch/pdf/10.1103/PhysRevResearch.6.033136)
 - [SPECIAL RELATIVITY DERIVED FROM CELLULAR AUTOMATA THEORY: The origin of the universal speed limit](https://arxiv.org/pdf/physics/9902034)
 - [Doubly-Special Relativity from Quantum Cellular Automata](https://arxiv.org/pdf/1310.6760)
 - [Exploring Rulial Space: The Case of Turing Machines](https://arxiv.org/pdf/2101.10907)
 - [The Problem of Distributed Consensus: A Survey](https://arxiv.org/pdf/2106.13591)

**Symbolic Computation**

 - [Finite element approximation of the Einstein tensor](https://arxiv.org/pdf/1703.09738)
 - [Computational General Relativity in the Wolfram Language using Gravitas I: Symbolic and Analytic Computation](https://arxiv.org/pdf/2308.07508)
 - [Symbolic Computation of Dynamics on Smooth Manifolds](https://hybrid-robotics.berkeley.edu/publications/WAFR2016_SymDynamics_Manifolds.pdf)
 - [Symbolic tensor calculus on manifolds: a SageMath implementation](https://arxiv.org/pdf/1804.07346)
 - [Symbolic Calculus for Value Boundary Problems on Manifolds and Edges](https://d-nb.info/1218377879/34) 

None of these approaches use a fully energy-driven, finite state automaton model similar to Entropic Engine.

---

## Acknowledgements

- **The Rebound Project**: A special thanks to the Rebound team for their incredible effort in developing and maintaining an efficient N-body simulation framework, which forms a crucial part of our work (https://rebound.readthedocs.io/en/latest/).
- **DeepSeek**: For their invaluable insights into assembly optimization, helping us refine our approach to performance improvements in C (https://github.com/deepseek-ai).
- **Stephen Wolfram** and his book **A New Kind of Science**: His work on cellular automata and computational approaches to physics has been a major inspiration for this project.
- **Matt Strassler** and his [website](https://profmattstrassler.com/) for his notion of "rate of flipping" as a mechanical effect rather than a mysterious field property. His analogy of a perpetual light in a mirrored box helped shape our understanding of how the rate of flipping relates to mass and acceleration effects. While this analogy has its limitations, it provides an intuitive way to think about how repeated interactions can lead to mass-like behavior in a confined system.
- **Dr. Jonathan Devor** for helping us understand the limitations of cellular automata with regard to the energy conservation.
- **Dr. Spencer H. Bryngelson** for his work on Floquet analysis, which was instrumental in extending our cellular automaton theory and understanding stability in energy-driven periodic systems.  
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

