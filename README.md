# Neuromorphic Computing Experiments

A collection of spiking neural network (SNN) simulations built from the ground up, exploring the foundations of neuromorphic computing.

## About
I'm an undergraduate ECE student researching neuromorphic hardware, SNNs, and edge AI. This repository documents my learning journey and experimental simulations.

## Simulations

### 01 — LIF Neuron Basics
Leaky integrate-and-fire neuron model simulated in Brian2. Covers single neuron 
dynamics, rate coding, and a 100-neuron synaptically connected network.

### 02 — STDP Learning
Spike-timing-dependent plasticity implemented between two neurons. Demonstrates 
real-time synaptic weight change — a fundamental biological learning rule.

### 03 — Event Camera N-MNIST Pipeline
Synthetic DVS event camera data generation and visualisation. Demonstrates 
event-based sensing and builds a full pipeline from raw events to a spiking 
neural network classifier — mirroring real neuromorphic hardware workflows.

### 04 — Balanced E/I STDP Memory Network
A 500-neuron excitatory/inhibitory network with STDP learning. Explores E/I 
balance, runaway excitation, sparse coding, and stochastic network behaviour. 
Achieves biologically realistic firing rates through parameter tuning.

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
