# The Fading Wire — Synaptic Plasticity as Short-Term Memory

**DataForge 2026 × Pathway — Pathway Track submission**

**Live artifact:** `public/index.html` (open directly in any browser, no server, no sign-in, no build step)

**Deployment Link:** https://synaptic-plasticity-bdh.vercel.app/

**Repository Link:** https://github.com/sp9284384-cyber/synaptic-plasticity-bdh

---

## The one-sentence claim

> Temporarily strengthening the connections between recently co-active units lets a network hold
> information as changing weights instead of new stored activations — but this memory decays over
> time and can be overwritten by unrelated activity (interference).

Full reasoning for why this is falsifiable: `docs/one_sentence_claim.md`

## Intended learner & prerequisites

- **Audience:** an undergraduate CS/ML student, or a data scientist unfamiliar with post-Transformer
  architectures, who knows what a neural network weight is but has not encountered Hebbian learning
  or BDH before.
- **Prerequisites:** basic familiarity with the idea of a "weight" in a neural network. No linear
  algebra, no backpropagation, no prior neuroscience background required.

## Learning objectives

After using this artifact, a learner should be able to:
1. State the one-sentence claim above in their own words.
2. Explain why `w = decay·w + η·x·y` produces "memory that fades unless reinforced."
3. Predict, before clicking, what triggering interference will do to an existing memory — and verify
   it against the live "Actual weight" readout.
4. Name where this exact mechanism appears in BDH (σ(i,j), Hebbian potentiation) and state one way
   the toy model differs from the real BDH architecture.

## Architecture of the artifact

| File | Role | Live / precomputed / animated |
|---|---|---|
| `public/index.html` | The entire interactive artifact: canvas rendering, sliders, buttons, Hebbian update loop | **Live** — the weight matrix, decay, and rendering are computed in real time in the browser on every tick. No canned animation. |
| `data/bdh_equations.md` | The exact BDH equations this project maps to, with citations | Reference material, not executed code |
| `data/primary_papers.json` | Required 2022–2026 primary sources | Reference material |
| `docs/one_sentence_claim.md` | The falsifiable claim and how the artifact tests it | Reference material |
| `docs/limitations.md` | Required disclosed limitation(s) / misconception | Reference material |
| `AI_DISCLOSURE.md` | Required AI-assistance and provenance disclosure | — |

There is no backend and no database. The entire simulation (a handful of neurons, one Hebbian
update rule, one decay rule) runs client-side in JavaScript — see `docs/limitations.md` and
`data/bdh_equations.md` for why this is an honest simplification and not a claim to reproduce BDH
itself.

## What's live vs. precomputed vs. illustrative

- **Live:** the entire neuron/synapse simulation. Every number shown (weight values, decay, the
  theoretical-vs-actual comparison) is computed on the fly from the sliders and buttons you press —
  nothing is a scripted animation.
- **Precomputed / reported (not run by us):** the BDH sparsity and "monosemantic synapse" findings
  cited in `data/bdh_equations.md` are the paper authors' own reported results from their trained
  models. We do not run or reproduce a BDH checkpoint.
- **Nothing here is a real BDH model.** This is explicitly disclosed in `docs/limitations.md`.

## How to reproduce

No install needed:
```bash
# from the repository root
open public/index.html         # macOS
xdg-open public/index.html     # Linux
start public\index.html        # Windows
```
Or simply double-click `public/index.html` in a file browser — it is a single self-contained HTML
file with no dependencies.

## Primary sources

See `data/primary_papers.json` for the full list with per-paper relevance notes. Core source for
the BDH module: Kosowski et al., "The Dragon Hatchling," arXiv:2509.26507.

## Credits & license

- Code, prose, and design: [your name / team names here].
- AI assistance disclosed in full in `AI_DISCLOSURE.md`.
- Code licensed under MIT (see `LICENSE`). Cited papers remain the property of their authors.