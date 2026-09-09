# Limitations and common misconceptions

## Limitation 1 — this is a toy, not BDH
The simulation uses 5 neurons and a symmetric (undirected) weight matrix for visual clarity. Real
BDH's σ(i,j) is directional (order of firing matters: i then j), lives in a much
higher-dimensional sparse space, and is never fully materialized even inside BDH-GPU (which
approximates it via a compact low-rank state ρ). This project illustrates the same *update rule*,
not a reproduction of BDH's actual architecture or scale.

## Limitation 2 — the interference model is simplified
This artifact demonstrates forgetting as "decay without reinforcement while a competing pattern is
reinforced instead." Real synaptic interference in a system like BDH would emerge from many neurons
sharing a limited, capacity-constrained activity budget across a much larger graph — a richer
phenomenon than the two-pattern, decay-dominated version shown here.

## Common misconception this artifact corrects
A common misconception is that "recurrent/fast-weight memory" means information is stored
somewhere explicit, the way a Transformer's KV-cache stores literal past tokens. This artifact
shows the opposite: there is no list of "things that happened" anywhere in the code — only a
weight matrix that grows and decays. The "memory" is not a record of the past; it is a present
physical quantity (synaptic strength) that happens to correlate with the past, and fades exactly
because nothing is being separately stored.
