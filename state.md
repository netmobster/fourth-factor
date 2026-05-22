# Fourth Factor — Session State
*Current working state. Overwritten each session. Not a permanent log — thoughts.md is the permanent record.*
*Last updated: 2026-05-22 — Session 1 close + red team review x2*

---

## WHERE WE ARE

Milestone 1 is approximately 65% complete. Architecture formalized. Two red team reviews completed (CPenn, Trust Insights). Architecture survived both. Four open problems identified for M2. Three additional findings from second red team pass filed below.

**What's done:**
- Three-layer system architecture locked (Layer 3 AI Interface → Layer 2 Spec → Layer 1 Validator)
- Two math layers identified: Layer 2 signal math (the hard problem) and Layer 1 crypto math (tractable once L2 defined)
- Signal extraction moment Type 01 (Itch/Beast) — variables defined, valid/invalid rules sketched
- Signal extraction moment Type 02 (Error Injection) — variables defined, Jay's correction signature partially confirmed (A/B mixed, direct, fast)
- Signal extraction moment Type 03 (Characteristic Unexpectedness) — concept defined, NOT fully specified
- Auth confirmed as ambient/continuous, not discrete login event
- Time confirmed as NOT a valid variable (async text) — sequence used instead
- Chaos injection must score LOW in cognitive confidence function
- Enrollment never ends — every session updates baseline
- Formal architecture filed:

```
FF_auth(O, B, R) = ZKP_verify(
  FE_extract(CC(R, B), B.envelope),
  O.commitment
)

CC(R, B) = w1·reframing_depth(R)
         + w2·reframe_sequence(R)
         + w3·error_injection_response(R)
         + w4·characteristic_unexpectedness(R, B)
         - w5·smoothness_penalty(R, B)
```

**What's NOT done — the thread that was live when we parked:**
`characteristic_unexpectedness` — the meta-variable that wraps all others. The hardest and most important variable to define.

Specific unresolved question: **What does `characteristic_unexpectedness` actually measure, and how does the cognitive confidence function distinguish "that's operator-specific friction" from "that's a bot injecting chaos"?**

This is the gate for completing M1 and moving to M2.

---

## LANGUAGE — USE THESE TERMS

**The operator object is not "preferences" or "memory" or "personality."**
It is a **structured latent behavioral manifold.**
Use this term in the paper. It's correct and it's defensible.

**The correct public framing:**
> "a probabilistic behavioral authentication framework for known operators under continuous interaction."

NOT: "unhackable," "proof of personhood," "true identity verification." Those get annihilated.
NOT: "I solved identity." Researchers hate this.
DO: name the unresolved theorem openly. Researchers respect that.

---

## KEY INSIGHT FROM SECOND RED TEAM — CHALLENGE GENERATOR

The operator model can generate adversarial challenges dynamically. This is the hidden strength:

```
challenge = f(operator_model, live_context, hidden_state)
```

Static biometrics are replayable. Dynamic cognition under perturbation may not be. The profile itself can generate personalized cognitive probes and identity-specific inconsistency traps that are impossible to precompute.

This partially addresses the challenge generator problem in concept. File for M2.

---

## OPEN PROBLEMS — FLAGGED FROM RED TEAM (file for M2)

**#1 — Model mimicry (the deepest attack)**
Frontier models are getting better at behavioral emulation. Architecture needs an explicit answer. Does not exist yet. Name it in M2.

**#2 — Entropy compression (empirical question, needs a sentence)**
Human behavioral patterns may compress more than they intuitively feel like. Not fatal — but must be acknowledged explicitly in the paper. Do not hand-wave it.

**#4 — False negatives under stress, grief, illness**
Product problem not crypto problem — but blocks deployment. Fallback auth flow needed. File for M2 product track.

**#5 — The challenge generator may be the invention**
Treat as a research problem on par with characteristic_unexpectedness. Not a downstream engineering problem.

---

## WHAT'S NEXT

**Immediate next session — finish M1:**
1. Resolve `characteristic_unexpectedness`
2. Formal valid/invalid rules for Types 02 and 03
3. One worked example per type
4. Lock Layer 2 downward interface format
5. Write `signal-extraction-moments.md` to repo

**Then M2:** Cognitive confidence number + challenge generator as primary research problem.
**Then M3:** Adversarial model. ~30% done in thoughts.md.
**Then M4:** Hard math. Cryptographer needed. @toxsec first candidate — already tagged.

---

## HOW TO RESUME

Tell ECHO: "fourth factor session" or "continue M1"

ECHO will:
1. Read this file
2. Read architecture.md
3. Read plan.md
4. Surface the unresolved `characteristic_unexpectedness` question
5. Pick up exactly where we left off

---

## OPEN ASIDES FROM THIS SESSION

- Send Anchar the Fourth Factor crypto stuff — waiting on Brad to confirm who Anchar is
- Brad 3 questions message — sent ✅
- Jessie WLL repo — sent ✅
- aboutjay-jodi.md — needs to be created. Jodi is a 15-year relationship, marketing brain, prom mom tonight.

---

*For permanent session log: thoughts.md*
*For architecture: architecture.md*
*For milestone plan: plan.md*

---

© Jeremy "Jay" Wright (Jeremy Wright) · wearecleardigital@gmail.com
Licensed under CC BY-NC-SA 4.0 (https://creativecommons.org/licenses/by-nc-sa/4.0/)
KNOWN-AI framework — free to use with attribution, no commercial use without a license.
