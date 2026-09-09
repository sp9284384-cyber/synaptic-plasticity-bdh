# BDH Equations Used in This Submission

All equations below are transcribed from primary sources and cited. None were run as live BDH
checkpoints — see AI_DISCLOSURE.md and README.md for what is live vs. illustrative in this submission.

## 1. The Hebbian potentiation rule (core mechanism this project illustrates)

From "The Dragon Hatchling: The Missing Link between the Transformer and Models of the Brain"
(Kosowski et al., arXiv:2509.26507):

> "Hebbian potentiation (fast weights / synaptic plasticity). If activity Y(i) at one neuron is
> followed by activity X(j) at another, the synaptic strength σ(i,j) increases proportionally:
> Y(i), X(j) → σ(i,j), i.e. 'neurons that fire together, wire together' interpreted as in-context
> fast-weight updates."

Mapping to this project's toy implementation (`public/index.html`, function `tick()`):

| BDH symbol | This project's symbol | Meaning |
|---|---|---|
| σ(i,j) | `w[i][j]` | Synaptic strength between neuron i and j |
| Y(i) | `active.has(i)` (as 1/0) | Presynaptic activity |
| X(j) | `active.has(j)` (as 1/0) | Postsynaptic activity |
| (implicit fast/slow separation) | `lr` (fast) vs. nothing (no slow weights modeled) | This project only models the fast-weight / working-memory layer, not BDH's separate long-term excitatory/inhibitory parameters |

## 2. Decay ("tension relaxes")

From the same paper's oscillator toy-model section:

> "A helpful toy analogy: imagine neurons as particles connected by elastic connectors (the
> synapses)... The elastic connectors accumulate tension (σ) when pulses co-occur across their
> endpoints. Tension relaxes over time unless reinforced."

This project's `decay` slider directly implements "tension relaxes over time unless reinforced" as
a per-tick multiplicative decay: `w = decay * w_old + lr * x * y`.

## 3. Sparsity (mentioned, not simulated at scale)

From the same paper: reported BDH-GPU runs show roughly 5% of neurons active per token, and
"individual synapses... often act as monosemantic detectors" (e.g. a "currency synapse," a
"country synapse"), consistent across languages (English/French, Europarl-trained models). This is
a **documented empirical result from the authors' trained models**, not something this toy
demo reproduces — it is cited as evidence for why Hebbian updates in real BDH are meaningful
rather than noisy, and is presented here as reported evidence, not a live experiment.

## 4. What this project explicitly does NOT claim

- This is not an official BDH implementation, and no BDH or BDH-CQ checkpoint was run.
- The toy network's weight matrix is symmetric/undirected, for visual clarity; BDH's real σ(i,j)
  is directional (i fires before j) and lives in a much higher-dimensional, sparse space that is
  never fully materialized (BDH-GPU approximates it via a compact low-rank state ρ, per Section 3
  of the paper).
- The "interference" shown here is a simplified, decay-dominated forgetting effect (an
  unreinforced synapse simply keeps decaying while a competing pattern is reinforced instead). Real
  BDH's interference would emerge from shared, capacity-limited neuron activity across a much larger
  network — this project illustrates the intuition, not a faithful capacity-constrained model.

## Sources

1. Kosowski, A. et al. "The Dragon Hatchling: The Missing Link between the Transformer and Models
   of the Brain." arXiv:2509.26507 (2025). https://arxiv.org/abs/2509.26507
2. Pathway. "BDH: The Dragon Hatchling architecture, explained" — Chapter 2: "From attention to
   synapses: deriving BDH." https://pathway.com/research/bdh-explainer
