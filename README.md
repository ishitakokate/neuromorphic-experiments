# Neuromorphic Computing Experiments

A collection of spiking neural network (SNN) simulations built from the ground up, exploring the foundations of neuromorphic computing.

## About
I'm an undergraduate ECE student researching neuromorphic hardware, SNNs, and edge AI. This repository documents my learning journey and experimental simulations.

## Status
Actively maintained alongside undergraduate coursework — updated roughly weekly...

## Simulations

### 01 — LIF Neuron Basics
Leaky integrate-and-fire neuron model simulated in Brian2. Covers single neuron 
dynamics, rate coding, and a 100-neuron synaptically connected network.

### 02 — STDP Learning
Spike-timing-dependent plasticity implemented between two neurons demonstrates 
real-time synaptic weight change — a fundamental biological learning rule.

### 03 — Event Camera N-MNIST Pipeline
Synthetic DVS event camera data generation and visualisation. Demonstrates 
event-based sensing and builds a full pipeline from raw events to a spiking 
neural network classifier — mirroring real neuromorphic hardware workflows.

### 04 — Balanced E/I STDP Memory Network
A 500-neuron excitatory/inhibitory network with STDP learning. Explores E/I 
balance, runaway excitation, sparse coding, and stochastic network behaviour. 
Achieves biologically realistic firing rates through parameter tuning.

### 05 — Coincidence Detector
A spiking circuit that fires only when two inputs arrive within a narrow 
time window of each other. Explores the relationship between membrane time 
constant (tau) and detection precision, modelling auditory sound-localisation 
circuits found in the brain (medial superior olive).

### 06 — Lava LIF Neuron Exploration
First experiments with Intel's Lava framework — the software stack used for 
the actual Loihi 2 neuromorphic hardware. It innvestigates Lava's discrete timestep 
behaviour, including a discovered one-step delay between membrane threshold 
crossing and spike reporting, which is verified through direct voltage probing.

### 07 — Lava Two-Neuron Network
Connects two LIF neurons via a `Dense` synapse process, investigating 
unexpected runaway firing behaviour through systematic voltage probing. 
Discovers and documents the role of the `du` (current decay) parameter,
revealing that `du=0` causes synaptic current to persist indefinitely 
rather than decay, producing continuous firing once enough current 
accumulates. This Demonstrates rigorous parameter characterisation through 
direct measurement.

### 08 — Lava STDP Learning Attempt
Attempts to implement STDP learning in Lava using `LoihiLearningRule` and 
`LearningDense`. Documents a reproducible deadlock when connecting 
post-synaptic spike feedback (`s_in_bap`) is confirmed as a known limitation 
of Lava's process-based architecture for recurrent learning circuits via 
official documentation. Demonstrates that feedforward-only connections 
produce zero weight change, confirming `s_in_bap` is functionally necessary 
for STDP despite the deadlock it triggers.

### 09 — Reward-Modulated STDP
Extends standard STDP with a global reward signal that gates whether spike-
timing-based weight updates actually occur. Demonstrates that two equally 
active pathways learn differently depending on reward, and shows reversal 
learning — the network dynamically reallocates learning to a newly rewarded 
pathway when reward contingencies flip mid-simulation. Directly inspired by 
neuromodulated learning rules discussed in the reading log's first paper.

### 10 — Eligibility Traces
Isolates and characterises the eligibility trace mechanism — the decaying 
synaptic memory that bridges spike coincidences and delayed reward signals. 
Demonstrates discrete time sampling behaviour, tau's control over the credit 
assignment window, and cumulative trace amplification from multiple spikes. 
Foundational for the delayed reward and reinforcement learning notebooks to follow.

### 11 — Delayed Reward Learning
Demonstrates temporal credit assignment — how learning degrades as the 
delay between spike coincidence and reward arrival increases, shows the 
1/e relationship between tau and learning at delay=tau, and compares 
three tau values to show direct control over the credit assignment window, also resolves two discrete-time simulation artifacts encountered during development.

### 12 — Reward Prediction Error (Schultz Experiment)
Reproduces Wolfram Schultz's classic dopamine experiment in a spiking 
network across three phases: unpredicted reward drives dopamine firing; 
after repeated cue-reward pairings, dopamine shifts to the predictive cue; 
when reward is omitted, dopamine fires at the cue but shows reduced activity 
at the expected reward time. Documents a structural threshold fixed point 
discovered during parameter tuning, resolved through biologically realistic 
stochastic noise.

### 13 — Project Dopamine Phase 1: Reward Dysregulation
Models dopamine receptor downregulation via adaptive firing thresholds in 
two parallel spiking networks exposed to different reward schedules — 
spaced naturalistic rewards vs engineered high-frequency variable-interval 
micro-rewards. Also quantifies the sensitivity divergence: the dysregulated system 
becomes 3x less responsive to identical stimuli. Phase 1 of an ongoing 
independent research project exploring computational psychiatry in SNNs.

### 14 — Synaptic Consolidation
Models the two-stage transition from fragile short-term plasticity to stable 
long-term memory using a fast plastic component (decays without reinforcement) 
and a slow stable component (persists indefinitely once written). Demonstrates 
that consolidated memories completely resist active reversal signals, directly 
explaining why dopamine dysregulation is hard to reverse — the foundation for 
Project Dopamine Phase 2.

### 15 — Project Dopamine Phase 2: Recalibration & Intervention
Tests three recovery strategies from a dysregulated state: abstinence, 
healthy rewards, and continued dysregulation. Quantifies a 5.9x hysteresis 
ratio — recovery takes nearly six times longer than dysregulation under 
identical conditions. Also documents two honest null results: homeostatic 
plasticity provides no meaningful recovery benefit (timescale mismatch), 
and intervention timing produces negligible differences in this model 
(threshold equilibrium reached too quickly). Phase 2 of Project Dopamine.

### 16 — Project Dopamine Phase 3: Beneficial Reward Engineering
Systematically maps 35 reward schedule parameter combinations (interval × 
variability) to identify conditions achieving high engagement without 
sensitivity collapse. Discovers a counterintuitive finding: at moderate 
intervals (200ms), HIGH variability preserves sensitivity better than low 
variability. Identifies an optimal schedule (200ms, var=0.9) achieving 78% 
of dysregulated engagement with 2.09x better sensitivity preservation — 
answering Project Dopamine's core question: yes, a neuromorphic agent can 
learn fast without getting fried. Completes the Project Dopamine arc across 
notebooks 13-16.

## Papers
A running reading log of papers and reviews informing this work lives in 
[`papers/reading_log.md`](papers/reading_log.md).

## Tools & Frameworks
- Python 3
- Brian2
- NumPy
- Matplotlib
- Jupyter Notebook

## Roadmap
- [x] Event-based vision with N-MNIST dataset
- [x] Larger STDP network with emergent memory
- [x] Intel Loihi 2 / Lava framework experiments
