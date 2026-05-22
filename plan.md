# Fourth Factor — Spec Development Plan
*Working document. README points here. This changes as the spec develops.*
*Last updated: 2026-05-22 — Deliverables for open source added.*

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

## On Open Sourcing

**Priority claim is already established.** The thesis article (May 22 2026) and this repo timestamp the idea publicly. Open sourcing the *spec* requires M4 cryptographer review first — publishing broken crypto is worse than not publishing.

**Who will care right now:** Almost nobody. The spec is only useful if you have a Known layer — a session-compounding behavioral operator profile rich enough to key from. SA is the only system building that. Open sourcing now is a priority claim, not an adoption play.

**What's needed to actually open source:**
1. The formal spec document (output of M1-M5)
2. Cryptographer validation of the math (M4 gate)
3. A reference implementation sketch (M5) — even toy code. Standards without working code get ignored.
4. A companion Substack piece: "The Standard" — what a KNOWN-AI open spec actually defines

**The gap from here to published:** 4-6 focused sessions. M1 → M2 → M3 → M4 (cryptographer) → M5 → publish. Not months. Sessions.

**Open source org question:** `known-ai/fourth-factor` vs staying at `netmobster/fourth-factor`. Decide at M6. No urgency.

---

## Milestone 1 — Signal Extraction Moment Definitions
**Status: IN PROGRESS — ~65% complete**
**Session type: Jay + ECHO**
**No cryptographer needed yet.**

What we're doing: defining the signal extraction moment types that Layer 3 reports to Layer 2. These are the observable interaction patterns that produce behavioral signal. NOT prompted challenges — observed moments in natural conversation.

**What's done:**
- Type 01 (Itch/Beast) — variables defined, valid/invalid rules sketched
- Type 02 (Error Injection) — variables defined, Jay's signature partially confirmed
- Type 03 (Characteristic Unexpectedness) — concept defined, NOT fully specified — THE OPEN THREAD
- Layer 3 interface format sketched
- Throwaway formula v0.0.1 filed in thoughts.md — 80% likely right per Jay

**What's remaining:**
- Resolve `characteristic_unexpectedness` — what it measures, how chaos injection is rejected
- Formal valid/invalid rules for Types 02 and 03
- Worked example for each type
- Confirm variable stability for Types 02 and 03
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

**Known hard problem flagged from Session 1:**
The weight math. w1..w5 as static learned weights is too simple. Weights need to be:
- Dynamic per emotional state (stressed operator weights differently than normal)
- Correlated across variables (reframing_depth and characteristic_unexpectedness are probably not independent)
- Resistant to weight inference attacks

This is the hardest part of M2. Don't skip it.

What done looks like:
- The cognitive confidence function f() defined
- How `characteristic_unexpectedness` wraps the other variables
- How `baseline_deviation_δ` is calculated
- How the function distinguishes operator-specific friction from synthetic chaos
- Weight math approach defined (even if approximate)
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
**GATE FOR OPEN SOURCE PUBLICATION.**

What we're doing: tolerance bounds, commitment scheme, entropy calculations. Operates on cognitive_confidence output from Layer 2.

Note: Layer 1 math is tractable once Layer 2 is defined. The crypto operations are well-understood. The hard part is knowing what to run them on.

What's needed before this session:
- M1, M2, M3 complete
- Cryptographer in the room (async counts)
- @toxsec first candidate — already tagged on the published article

What done looks like:
- Tolerance bounds defined and justified
- Entropy calculations for behavioral input
- Commitment scheme parameters
- Explicit statement of security assumptions
- Section that says what breaks the math and under what conditions
- Cryptographer has signed off or flagged specific issues

---

## Milestone 5 — Reference Implementation Sketch
**Status: NOT STARTED**
**Session type: Jay + ECHO**

**Why this matters for open source:** Standards without working code get ignored. This doesn't need to be production code — it needs to be enough that someone else could build toward the standard.

What we're doing: describing how a compliant AI system implements Layer 3. ECHO/Imprint as the reference. What any other AI would need to provide. Enough that a competent engineer could start implementing.

What done looks like:
- Enrollment flow: how a new operator establishes their behavioral commitment
- Authentication flow: how signal extraction → Layer 2 → Layer 1 → vault works end-to-end
- SA Known layer cited as reference without exposing proprietary detail
- What a non-SA implementation would need to provide
- Toy pseudocode or reference diagram (not production code)

---

## Milestone 6 — Publish
**Status: NOT STARTED**
**Gate: M4 cryptographer review complete.**

Open standard. Spec free. Known layer proprietary. Same move W3C made with Solid.

Decisions to make at this milestone:
- known-ai GitHub org vs netmobster/fourth-factor (current)
- License — CC BY-NC-SA 4.0 or something more permissive for a standard
- Companion Substack piece: "The Standard" — what a KNOWN-AI open spec actually defines
- Announce to @toxsec and security community for public review

---

## Session Log

**May 22 2026 — Session 1 (full day)**
Conceived the Fourth Factor. Published thesis article. Created repo. Wrote README, plan, thoughts, architecture, state. Defined three-layer system architecture. Identified two distinct math layers. Defined three signal extraction moment types with variables. Confirmed auth is ambient/continuous not discrete. Confirmed any AI can implement Layer 3. Confirmed time is not a valid variable in async text (replaced with sequence). Confirmed chaos injection must score LOW. Confirmed enrollment never ends. Filed throwaway formula v0.0.1. Jay assessed formula as ~80% likely right if math holds. Weight math flagged as needing serious work in M2.

Status entering Session 2: M1 ~65% complete. M3 ~30% complete. Open thread: `characteristic_unexpectedness`.

---

© Jeremy "Jay" Wright (Jeremy Wright) · wearecleardigital@gmail.com
Licensed under CC BY-NC-SA 4.0 (https://creativecommons.org/licenses/by-nc-sa/4.0/)
KNOWN-AI framework — free to use with attribution, no commercial use without a license.
