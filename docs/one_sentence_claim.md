# The one-sentence claim

> Temporarily strengthening the connections between recently co-active units lets a network hold
> information as changing weights instead of new stored activations — but this memory decays over
> time and can be overwritten by unrelated activity (interference).

## Why this is falsifiable

The artifact lets a learner directly test each half of the claim:

- **"Holds information without a stored activation"** — reinforce pattern A, stop firing it, and
  watch the synapse between neurons 0 and 1 stay above zero (evidence of retained information)
  purely because of `w`, with no separate memory array anywhere in the code holding "pattern A
  happened."
- **"Decays over time"** — with no interference at all, the synapse strength still falls every tick
  once reinforcement stops (visible directly via the "Actual weight" readout falling away from the
  flat "Theoretical weight" line).
- **"Can be overwritten by unrelated activity"** — trigger pattern B (which shares neuron 2 with
  pattern A) and then re-test recall of A. If the claim is false, interference should have no
  measurable effect on A's synapse strength. It does.

If a learner sets decay to 0.999 and interference does nothing to A's weight, or if decay never
reduces an unreinforced synapse, the claim would be falsified by this exact artifact — which is the
bar the brief sets for a valid claim.
