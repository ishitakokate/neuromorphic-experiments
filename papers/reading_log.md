# Reading Log

A running log of papers and reviews read during ongoing neuromorphic computing 
self-study, with summaries and connections to notebooks in this repository.

---

## Neuromorphic Computing 2025: Current State of the Art
**Source:** humanunsupervised.com (review, 2025)  
**Date read:** June 2026

### Summary
A comprehensive review covering neuromorphic hardware (Intel Loihi, IBM TrueNorth, 
SpiNNaker, memristors, spintronics, photonics, 2D materials) and algorithmic 
advances (SNNs, surrogate gradient training, biologically plausible learning 
rules) from 2019–2024.

### Key connections to my notebooks
- **Section 3.1 (Digital Neuromorphic Chips):** Directly contextualizes notebooks 
  06–08 (Lava/Loihi work) — Loihi 2 has ~1 million neurons per chip with on-chip 
  spike-driven learning rules.
- **Section 4.1 (Temporal Coding):** Connects to notebook 03 (event camera) and 
  notebook 05 (coincidence detector) — confirms that event-based vision sensors 
  inherently operate on spike timing rather than averaged rates.
- **Section 4.3 (Biologically Plausible Learning Rules):** Directly extends 
  notebooks 02, 04, and 08 (STDP work). Introduced **e-prop** (Bellec et al., 2020) 
  — a more scalable local learning algorithm than plain STDP, using eligibility 
  traces. Also introduced **reward-modulated STDP**, combining local learning 
  with a global reward signal — this inspired notebook 09.

### New concepts learned
- **Memristor crossbar arrays:** Physically compute weighted sums via Ohm's Law 
  (I = V × conductance) and Kirchhoff's Current Law (currents summing at a 
  junction) — the matrix-vector multiplication happens in the physics itself, 
  not as a calculated operation. This is the core mechanism behind in-memory 
  computing's energy efficiency.
- **e-prop (eligibility propagation):** Trains recurrent SNNs using only locally 
  available information per synapse, unlike backpropagation which needs global 
  network information. Approaches backprop-through-time performance on tasks 
  like speech recognition.
- **Hybrid learning approaches:** Using STDP for unsupervised pre-training of 
  feature representations, then fine-tuning with surrogate gradient supervised 
  learning — combines unsupervised adaptation with task-specific accuracy.

### Open questions / follow-ups
- Want to eventually implement full e-prop as a larger project (multi-week scope).
- Notebook 09 will implement reward-modulated STDP as an accessible first step 
  toward the reward-signal-driven learning described in Section 4.3.

### Citation
Source paper: "Neuromorphic Computing 2025: Current SotA" (2025-09-01), 
humanunsupervised.com.