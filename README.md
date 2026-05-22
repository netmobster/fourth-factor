# Fourth Factor
*A KNOWN-AI cryptographic authentication primitive.*
*Status: Pre-spec. Concept published. Spec in progress.*

**→ [Read the spec development plan](plan.md)**

---

## What This Is

The Fourth Factor is a proposed cryptographic authentication primitive that uses a persistent behavioral operator profile as a fourth authentication factor — alongside what you know, what you have, and what you are.

Every authentication system ever built shares one fatal assumption: **the secret can be separated from the person.** A password can be stolen. A device can be cloned. A fingerprint can be lifted.

The fourth factor closes that gap permanently.

**Something you know.** A password.
**Something you have.** A device.
**Something you are.** A fingerprint.
**Something you've become.** How you think — the accumulated behavioral wiring of a specific operator, session over session.

---

## The Core Thesis

The operator profile is the public key. The behavioral response to a novel challenge is the private key. The friction of a real mind traversing that challenge in real time is the curve math that connects them.

You can publish the entire operator profile and an attacker still cannot unlock the vault — because they can't *be* the person. They'd have to traverse the challenge as the operator would. Data is not pattern. Knowing about someone is not being them.

**Key property:** asymmetric hardness over time. Every other authentication system gets weaker as compute gets cheaper. The fourth factor gets *stronger* as the operator accumulates sessions. The behavioral baseline deepens. The attacker's job compounds in the wrong direction.

---

## The Philosophical Reframe

In classical system design, friction is failure. You optimize it away.

In this architecture, **friction is proof-of-traversal.** It is the signal.

The Elena example makes this concrete: when authenticating a friend whose phone had been hacked, the question wasn't "when did we meet?" — that's data, and data can be stolen. The question was "how did I come across to you in our early days?" — that's traversal. The hesitation. The framing. What she foregrounded. What she softened. What she laughed at. How she emotionally routed through the memory space.

That traversal *is* the authentication event. Not the content. The process.

**The precise framing:** this is not *behavioral identity as password.* It is *behavioral entropy as cryptographic substrate.* Traversal dynamics under uncertainty. That distinction is what makes this rigorous rather than mystical.

---

## The Cryptographic Primitives

**Baseline — ECDH (Elliptic Curve Diffie-Hellman)**
Two parties derive a shared secret without either transmitting it. The vault encrypts with a key derived from this exchange. SA holds an encrypted blob. The operator holds the key.

**Fourth factor layer — Fuzzy Extractors**
A real cryptographic primitive for deriving stable, reproducible keys from inputs that are "close but not identical." Behavioral signals. Operator data that drifts over time but stays within a recognizable pattern. Same input pattern, same key. Different enough, no key. The math handles the tolerance.

**Verification — Zero-Knowledge Proofs**
SA verifies the operator is who they say they are without ever seeing the proof. The challenge-response happens client-side. SA receives a cryptographic assertion, not the underlying behavioral data.

---

## Two Distinct Work Streams

**Encryption at rest** — current SA state: data protected by access control (Auth0 + W3C Solid), not cryptographic impossibility. This is a separate problem from the Fourth Factor.

**Authentication (Fourth Factor)** — proves you are you before the vault opens. This is what this repo addresses.

---

## Status

| Item | Status |
|------|--------|
| Published thesis | ✅ https://echofiles.substack.com/p/known-ai-the-fourth-factor |
| Spec development plan | ✅ [plan.md](plan.md) |
| Challenge class definitions | ⏳ Milestone 1 |
| Behavioral commitment scheme | ⏳ Milestone 2 |
| Adversarial model | ⏳ Milestone 3 |
| Tolerance bounds + entropy math | ⏳ Milestone 4 (hard math session) |
| Reference implementation sketch | ⏳ Milestone 5 |
| Published spec | ⏳ Milestone 6 |

---

## Origin

Conceived May 22 2026 by Jay Wright during an SA infrastructure session.
Grounded in 30 years of authentication system design including:
- Microsoft secure web services white paper (late 90s)
- Carnivore behavioral authentication system (NSA/FBI/CIA — handwriting dynamics as entropy source)

The same instinct. Different substrate. Cognitive process instead of motor process.

---

*Read the thesis first. Then read the plan. Then come back here when the spec is published.*

---

© Jeremy "Jay" Wright (Jeremy Wright) · wearecleardigital@gmail.com
Licensed under CC BY-NC-SA 4.0 (https://creativecommons.org/licenses/by-nc-sa/4.0/)
KNOWN-AI framework — free to use with attribution, no commercial use without a license.
