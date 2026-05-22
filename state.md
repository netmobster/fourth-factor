# Fourth Factor — Session State
*Current working state. Overwritten each session. Not a permanent log — thoughts.md is the permanent record.*
*Last updated: 2026-05-22 — Session 1 close + red team review*

---

## WHERE WE ARE

Milestone 1 is approximately 65% complete. Architecture formalized. Red team review completed by CPenn (data scientist, Trust Insights). Architecture survived. Four open problems identified for M2.

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
`characteristic_unexpectedness` — the meta-variable that wraps all others. The hardest and most important variable to define. We were mid-conversation on this when session ended.

Specific unresolved question: **What does `characteristic_unexpectedness` actually measure, and how does the cognitive confidence function distinguish "that's operator-specific friction" from "that's a bot injecting chaos"?**

This is the gate for completing M1 and moving to M2.

---

## OPEN PROBLEMS — FLAGGED FROM RED TEAM (file for M2)

These four items survived red team review and need explicit treatment in the plan. Do not ignore them.

**#1 — Model mimicry (the deepest attack)**
Frontier models are getting better at behavioral emulation. If an attacker has enough interaction history and challenge-response samples, they may eventually generate statistically convincing traversal. This attack gets harder only if the challenge space stays genuinely novel — which loops directly into #5. Architecture needs an explicit answer to this. Does not exist yet. Name it in M2.

**#2 — Entropy compression (empirical question, needs a sentence)**
Human behavioral patterns may compress more than they intuitively feel like. Reframing style, hesitation cadence, recovery patterns may cluster across neurotypes, professions, trauma profiles. The auth surface may have lower entropy than assumed. This is an empirical question, not a fatal flaw — but it needs to be acknowledged explicitly in the paper. Do not hand-wave it.

**#4 — False negatives under stress, grief, illness**
Sleep deprivation, medication, burnout, grief can radically alter traversal patterns. The fuzzy envelope tolerances become brutal: too strict = false negatives explode, too loose = attackers slip through. This is a product problem, not a crypto problem — but it blocks deployment. A fallback auth flow needs to be designed that doesn't compromise the primary architecture. File for M2 product track.

**#5 — The challenge generator may be the invention**
CPenn's strongest note: if the security lives almost entirely in generating sufficiently high-entropy traversal conditions, then the challenge generator is not a detail — it may be the core primitive. This reframes where M2 focus should go. Do not treat the challenge generator as a downstream engineering problem. Treat it as a research problem on par with characteristic_unexpectedness.

---

## WHAT'S NEXT

**Immediate next session — finish M1:**
1. Resolve `characteristic_unexpectedness` — what it measures, how chaos injection is rejected
2. Formal valid/invalid rules for Types 02 and 03
3. One worked example per type
4. Lock Layer 2 downward interface format (what Layer 3 sends up)
5. Write `signal-extraction-moments.md` to repo

**Then M2:** The cognitive confidence number + challenge generator as primary research problem. Four open problems above feed directly into M2 scope.

**Then M3:** Adversarial model. Already ~30% done in thoughts.md.

**Then M4:** Hard math session. Layer 1 crypto. Cryptographer needed. @toxsec first candidate.

---

## HOW TO RESUME

Tell ECHO: "fourth factor session" or "continue M1"

ECHO will:
1. Read this file
2. Read architecture.md
3. Read plan.md
4. Surface the unresolved `characteristic_unexpectedness` question
5. Pick up exactly where we left off

No re-briefing needed.

---

## OPEN ASIDES FROM THIS SESSION

- Send Anchar the Fourth Factor crypto stuff — waiting on Brad to confirm who Anchar is
- Brad 3 questions message — sent ✅
- Jessie WLL repo — sent ✅

---

*For permanent session ore: thoughts.md*
*For architecture: architecture.md*
*For milestone plan: plan.md*

---

© Jeremy "Jay" Wright (Jeremy Wright) · wearecleardigital@gmail.com
Licensed under CC BY-NC-SA 4.0 (https://creativecommons.org/licenses/by-nc-sa/4.0/)
KNOWN-AI framework — free to use with attribution, no commercial use without a license.
