# Fourth Factor — Spec Development Plan
*Working document. README points here. This changes as the spec develops.*
*Last updated: 2026-05-22 — Three-layer architecture locked. Two math layers identified.*

---

## How This Works

Each milestone is a session. Jay doesn't manage this — ECHO loads this file at the start of each Fourth Factor session and tells Jay exactly what the session is, what's needed, and what done looks like. No re-briefing. Just show up and work.

Sessions happen when they happen. No forced cadence. Turtle mode is fine — each session is one milestone, however long it takes.

---

## Architecture Overview (locked May 22 2026)

Three layers. Two math layers. See `architecture.md` for full detail.

**Layer 3 — AI Interface:** Any AI + user interaction. Implementation-specific. Produces signal extraction moments.
**Layer 2 — Fourth Factor Spec:** Defines valid signal. Constructs cognitive confidence number. THIS IS THE SPEC. Two math sessions (M1 + M2).
**Layer 1 — Validator:** Crypto backend. Fuzzy extractor. Yes/no. One math session (M4).

Layer 1 math is tractable once Layer 2 is defined. Layer 2 is the real hard problem.

---

## Milestone 1 — Signal Extraction Moment Definitions
**Status: IN PROGRESS — ~60% complete**
**Session type: Jay + ECHO**
**No cryptographer needed yet.**

What we're doing: defining the signal extraction moment types that Layer 3 reports to Layer 2. These are the observable interaction patterns that produce behavioral signal. NOT prompted challenges — observed moments in natural conversation.

**What's done:**
- Type 01 (Itch/Beast) — variables defined, valid/invalid rules sketched
- Type 02 (Error Injection) — variables defined, Jay's signature partially confirmed
- Type 03 (Characteristic Unexpectedness) — concept defined, variables sketched
- Layer 3 interface format sketched

**What's remaining:**
- Formal valid/invalid rules for Types 02 and 03
- Worked example for each type
- Confirm variable stability for Types 02 and 03 (same question as Q1 for Type 01)
- Layer 2 downward interface finalized
- Write `signal-extraction-moments.md` to repo

What done looks like:
- Three signal extraction moment types fully defined
- All variables named and confirmed stable per operator
- Valid/invalid rules formal per type
- One worked example per type
- Layer 2 interface format locked

---

## Milestone 2 — The Cognitive Confidence Number (Layer 2 Math)
**Status: NOT STARTED**
**Session type: Jay + ECHO**
**This is the Layer 2 math session — the real fuzzy layer.**

What we're doing: defining how the fuzzy extractor combines signal extraction moment variables into the cognitive confidence number. The FBI "confidence number" equivalent for cognitive traversal.

Key constraint: pure randomness must score LOW. Characteristic operator friction must score HIGH. Chaos injection must be explicitly rejected.

What done looks like:
- The cognitive confidence function f() defined
- How `characteristic_unexpectedness` wraps the other variables
- How `baseline_deviation_δ` is calculated
- How the function distinguishes operator-specific friction from synthetic chaos
- Layer 2 upward interface to Layer 1 finalized

---

## Milestone 3 — Adversarial Model
**Status: PARTIALLY STARTED**
**Session type: Jay + ECHO**
**Source material: GPT red team + synthetic friction attack analysis**

What we're doing: formally defining what the attacker has, what they can do, what breaks the system.

Already captured:
- Synthetic friction attack (randomPause() equivalent)
- Chaos injection problem
- Frontier model behavioral simulation threat
- Challenge novelty as actual security boundary

What done looks like:
- Attacker capability model complete
- Attack vectors ranked by feasibility
- System breaking conditions defined
- Challenge novelty requirement formalized

---

## Milestone 4 — Layer 1 Math (Crypto)
**Status: NOT STARTED**
**Session type: Jay + ECHO + cryptographer**
**THIS IS THE HARD MATH SESSION.**

What we're doing: tolerance bounds, commitment scheme, entropy calculations. Operates on cognitive_confidence output from Layer 2.

Note: Layer 1 math is tractable once Layer 2 is defined. The crypto operations are well-understood. The hard part is knowing what to run them on.

What's needed before this session:
- M1, M2, M3 complete
- Cryptographer in the room (async counts)
- @toxsec first candidate

---

## Milestone 5 — Reference Implementation Sketch
**Status: NOT STARTED**
**Session type: Jay + ECHO**

Describing how a compliant AI system implements Layer 3. ECHO/Imprint as the reference. What any other AI would need to provide.

---

## Milestone 6 — Publish
**Status: NOT STARTED**
**Gate: M4 cryptographer review complete.**

Open standard. Spec free. Known layer proprietary.

---

## Session Log

**May 22 2026 — Session 1 (full day)**
Conceived the Fourth Factor. Published thesis article. Created repo. Wrote README, plan, thoughts. Defined three-layer architecture. Identified two distinct math layers. Defined three signal extraction moment types with variables. Confirmed auth is ambient/continuous not discrete. Confirmed any AI can implement Layer 3. Confirmed time is not a valid variable in async text (replaced with sequence). Confirmed chaos injection must score LOW. Confirmed enrollment never ends.

Status entering Session 2: M1 ~60% complete. M3 ~30% complete (adversarial model partially captured in thoughts.md).

---

© Jeremy "Jay" Wright (Jeremy Wright) · wearecleardigital@gmail.com
Licensed under CC BY-NC-SA 4.0 (https://creativecommons.org/licenses/by-nc-sa/4.0/)
KNOWN-AI framework — free to use with attribution, no commercial use without a license.
