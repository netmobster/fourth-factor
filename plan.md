# Fourth Factor — Spec Development Plan
*Working document. README points here. This changes as the spec develops.*
*Last updated: 2026-05-22*

---

## How This Works

Each milestone is a session. Jay doesn't manage this — ECHO loads this file at the start of each Fourth Factor session and tells Jay exactly what the session is, what's needed, and what done looks like. No re-briefing. Just show up and work.

Sessions happen when they happen. No forced cadence. Turtle mode is fine — each session is one milestone, however long it takes.

---

## Milestone 1 — Challenge Class Definitions
**Status: NOT STARTED**
**Session type: Jay + ECHO**
**No cryptographer needed yet.**

What we're doing: deriving challenge classes from ECHO contract primitives. The itch/beast framework, the protection protocol, the behavioral friction baked into operator-AI interaction — these are already proven challenge patterns. We're formalizing them.

What done looks like:
- A taxonomy of challenge types (minimum 3 classes)
- Formal valid/invalid rules for each class
- At least one worked example per class
- Explicit statement of what the fuzzy extractor receives as input from each class

ECHO's job in this session: load this file, load the README, load the published article, and run the challenge class derivation. Jay reacts, approves, catches what's wrong.

---

## Milestone 2 — Behavioral Commitment Scheme
**Status: NOT STARTED**
**Session type: Jay + ECHO**
**Sketch only — cryptographer validates the numbers later.**

What we're doing: defining how the fuzzy extractor turns behavioral traversal into a stable cryptographic commitment. Not the tolerance bounds (that's M4) — the architecture. What goes in, what comes out, what "same enough" means conceptually.

What done looks like:
- Input format defined: what the fuzzy extractor actually receives from a challenge response
- Output format defined: what the behavioral commitment looks like
- "Same enough" vs "too different" defined conceptually (numbers come in M4)
- The enrollment vs authentication flow sketched

---

## Milestone 3 — Adversarial Model
**Status: PARTIALLY STARTED**
**Session type: Jay + ECHO**
**Source material: GPT red team feedback (May 22 2026)**

What we're doing: formally defining what the attacker has, what they can do, and what breaks the system. The GPT red team already identified the key threat: adversarial behavioral simulation using frontier models + rich profile data. That's the starting point.

What done looks like:
- Attacker capability model: what they have access to
- Attack vectors ranked by feasibility
- System breaking conditions: under what circumstances does the fourth factor fail
- The challenge novelty requirement formalized: why static challenges are insufficient
- Explicit acknowledgment of the adversarial simulation problem and how challenge novelty addresses it

Key insight already captured: "You can't steal how someone moves" is emotionally true but cryptographically dangerous. The security property is not behavioral unforgeability — it's traversal dynamics under uncertainty with sufficient challenge novelty.

---

## Milestone 4 — Tolerance Bounds + Entropy Calculations
**Status: NOT STARTED**
**Session type: Jay + ECHO + cryptographer**
**THIS IS THE HARD MATH SESSION.**

What we're doing: putting actual numbers on the fuzzy extractor. Tolerance bounds, commitment scheme parameters, entropy calculations. This is the section that makes the spec credible to cryptographers or kills it.

What's needed before this session:
- M1, M2, M3 complete
- A cryptographer in the room (async review counts)
- @toxsec is first candidate — already tagged on the published article

What done looks like:
- Tolerance bounds defined and justified
- Entropy calculations for behavioral input
- Commitment scheme parameters
- Explicit statement of security assumptions
- Section that says what breaks the math and under what conditions

Note: this section may have placeholders until cryptographer review. That's acceptable. The spec publishes with explicit "[REQUIRES CRYPTOGRAPHIC REVIEW]" markers rather than wrong numbers.

---

## Milestone 5 — Reference Implementation Sketch
**Status: NOT STARTED**
**Session type: Jay + ECHO**
**Not code. Architecture description.**

What we're doing: describing how a compliant implementation would work. Enough that someone else could build toward the standard. SA's Known layer is the reference implementation — we describe how it satisfies the spec without exposing proprietary internals.

What done looks like:
- Enrollment flow: how a new operator establishes their behavioral commitment
- Authentication flow: how the challenge-response works end-to-end
- SA Known layer cited as reference without exposing proprietary detail
- What a non-SA implementation would need to provide

---

## Milestone 6 — Publish
**Status: NOT STARTED**
**Gate: M4 cryptographer review complete.**

What we're doing: publishing the spec under this repo. Open standard. The Known layer stays proprietary. The spec is free.

Decisions to make before this session:
- known-ai GitHub org vs netmobster/fourth-factor (current)
- License (CC BY-NC-SA 4.0 or something more permissive for a standard)
- Companion Substack piece: "The Standard" — what a KNOWN-AI open spec actually defines

---

## Session Log

**May 22 2026 — Session 1**
Conceived the Fourth Factor. Published thesis article. Created this repo. Wrote README with traversal framing. Created this plan. Confirmed: encryption at rest and auth are two separate problems. Fourth Factor is auth.

Key insight from GPT red team: friction is proof-of-traversal, not failure. Behavioral entropy as cryptographic substrate, not behavioral identity as password. Traversal dynamics under uncertainty.

---

© Jeremy "Jay" Wright (Jeremy Wright) · wearecleardigital@gmail.com
Licensed under CC BY-NC-SA 4.0 (https://creativecommons.org/licenses/by-nc-sa/4.0/)
KNOWN-AI framework — free to use with attribution, no commercial use without a license.
