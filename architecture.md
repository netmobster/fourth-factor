# Fourth Factor — System Architecture
*Definitive architecture document. Updated as understanding evolves.*
*Last updated: 2026-05-22 — Session 1*

---

## The Three System Layers

The Fourth Factor is not one thing. It is three distinct layers with clean interfaces between them.

```
User ↔ AI System (Layer 3 — implementation)
              ↓ signal extraction moments
         Fourth Factor Spec (Layer 2 — the standard)
              ↓ formatted signal + confidence score
         Validator (Layer 1 — crypto backend)
              ↓ yes / no
         Vault opens or stays closed
```

---

## Layer 1 — The Validator (crypto backend)

**What it does:** Receives formatted signal from Layer 2. Runs fuzzy extractor. Applies tolerance bounds. Returns binary: authenticated or not.

**What lives here:**
- ECDH key derivation
- Fuzzy extractor tolerance bounds
- Zero-knowledge proof construction
- Entropy calculations
- The behavioral commitment (enrolled baseline)

**The math:** Hard crypto math. This is M4. Needs cryptographer.

**Key property:** Oddly tractable once Layer 2 is defined. Layer 1 is doing well-understood crypto operations on whatever Layer 2 produces. The hard part is Layer 2, not Layer 1.

**Interface up:** Receives `fourth_factor_signal` struct from Layer 2. Returns `{authenticated: bool, confidence: float, session_token: string}`.

---

## Layer 2 — The Fourth Factor Spec (the standard)

**What it does:** Defines what valid behavioral signal looks like. Defines signal extraction moment types. Constructs the cognitive confidence number from raw variables. Formats signal for Layer 1.

**What lives here:**
- Signal extraction moment definitions (the challenge classes)
- Variable definitions (reframing_depth, reframe_sequence, etc.)
- The cognitive confidence number construction (the fuzzy Layer 2 math)
- Valid/invalid signal rules
- The downward interface: what Layer 3 must send up
- The upward interface: what Layer 2 sends to Layer 1

**The math:** Layer 2 math. The fuzzy layer. How you turn messy human behavioral signal into a clean cryptographic input. This is the real hard problem. M1 defines the variables. M2 defines how they combine.

**Key constraint:** Must explicitly reject chaos as valid input. Pure randomness scores LOW. Characteristic friction scores HIGH. The extractor measures operator-specific friction distribution, not friction presence.

**Interface down (from Layer 3):**
```
{
  session_id: string,
  operator_id: string,
  signal_moments: [
    {
      moment_type: string,        // e.g. "itch_beast", "error_injection"
      variables: {},              // moment-type specific
      sequence_position: int,     // position in conversation
      timestamp: int              // relative, not absolute
    }
  ]
}
```

**Interface up (to Layer 1):**
```
{
  operator_id: string,
  cognitive_confidence: float,    // 0.0 - 1.0
  signal_vector: [],              // normalized variable array
  session_entropy: float,         // how much novel signal this session produced
  moment_count: int               // number of signal moments extracted
}
```

---

## Layer 3 — The AI Interface (implementation)

**What it does:** Works with the user in the system's native interaction style to generate signal extraction moments. Reports moments to Layer 2 in the standard format.

**What lives here:** Nothing in the spec. This is implementation-specific.
- In ECHO/Claude: conversation-native. Itch/beast patterns, error corrections, unexpected answers emerge organically.
- In Imprint: Imprint-native interaction.
- In any future system: that system's native interaction.

**Key insight:** Auth is NOT a discrete login moment. It is ambient continuous signal extraction woven into normal interaction. The AI doesn't prompt the user to authenticate. It observes the conversation and extracts signal. After N signal extraction moments with sufficient confidence, the vault opens. The user never sees a login prompt.

**Key insight 2:** Any AI that can read the Fourth Factor spec can implement Layer 3. The spec is AI-readable by design. Same layer as MCP, llms.txt, robots.txt. A protocol for AI-to-system authentication using operator behavioral profile as key material.

**Interface up (to Layer 2):** Must produce `signal_moments` array in the format Layer 2 defines. How those moments are generated is the implementation's business.

---

## The Two Math Layers

**Layer 2 math — signal math (the fuzzy layer):**
What makes a valid signal extraction moment. How you measure variables. How you combine them into the cognitive confidence number. How you distinguish characteristic friction from synthetic chaos. This is the math that turns messy human behavior into a clean cryptographic input.

This is M1 (variables) + M2 (combination) in the plan.

**Layer 1 math — crypto math:**
Fuzzy extractor tolerance bounds. ECDH key derivation. ZK proof construction. Entropy calculations. Operates on whatever Layer 2 produces. Well-understood crypto once Layer 2 is defined.

This is M4 in the plan. Needs cryptographer.

**Dependency:** Layer 2 math must be defined first. Layer 1 operates on Layer 2 output. Garbage in, garbage out — even perfect crypto.

---

## Signal Extraction Moment Types (Layer 2 — M1)

### Type 01 — Itch/Beast
*Source: ECHO itch/beast framework*

A situation with surface meaning and deeper meaning. Observed naturally in conversation — not prompted.

**Variables:**
- `reframing_depth` — how many layers down unprompted (integer, stable per operator)
- `reframe_sequence` — did they reframe before or after attempting to answer (sequence, not time)
- `beast_named_before_solution` — did they name obstacle before fix (boolean)
- `unprompted_reframe_count` — how many reframes without being asked (integer)

**Valid signal:** Deep unprompted reframing, beast named before solution, consistent depth across sessions.
**Invalid signal:** Surface acceptance, factual recall only, binary response, prompted reframing only.

**Confirmed stable:** `reframing_depth` is stable per operator across situations. State (stressed/relaxed) affects speed and style, not depth. Baseline calibrates for state variance.

### Type 02 — Error Injection
*Source: ECHO rage/anti-mode framework*

A wrong premise embedded in the interaction. Observed naturally when system or interlocutor makes an error. Can also be deliberately seeded.

**Variables:**
- `error_detection_latency` — how quickly the error was caught (sequence position, not time)
- `correction_sequence` — correct-first-then-answer (A) vs answer-through-correction (B)
- `correction_directness` — named wrong explicitly vs silent fix
- `correction_confidence` — stated correction vs questioned correction
- `error_injection_response` — composite of above

**Jay's signature:** A/B mixed — sometimes explicit correction first, sometimes embedded. Direct, not hedged. Fast detection. This distribution is the signal.

**Valid signal:** Characteristic correction pattern matching enrolled baseline distribution.
**Invalid signal:** Missed error entirely, overcorrection, wrong sequence distribution for this operator.

### Type 03 — Characteristic Unexpectedness
*Source: Jay insight — "unexpected answer, variance tuned to 12"*

Not random chaos. Not predictable correctness. The specific flavor of unexpected that is recognizably this operator. The meta-variable that wraps all others.

**Variables:**
- `characteristic_unexpectedness` — does the response surprise in an operator-specific way
- `unexpectedness_distribution` — does the surprise pattern match enrolled operator's surprise signature

**The distinction:** A bot can inject chaos. It cannot inject *your* chaos. The AI clocking "that's funky" is the fuzzy extractor noticing the unexpectedness distribution matches the enrolled operator.

**Valid signal:** Surprising in a way that matches the operator's characteristic surprise signature.
**Invalid signal:** Random chaos (wrong distribution), predictable correctness (no signal), surprising in a non-operator-specific way.

**Design note:** This is the meta-wrapper. `characteristic_unexpectedness` may be the cognitive confidence number itself, with all other variables feeding into it.

---

## The Cognitive Confidence Number (Layer 2 — M2)

Not yet defined. This is the FBI "confidence number" equivalent — the meta-variable that combines all signal extraction moment variables into a single extractable number for Layer 1.

Candidate structure:
```
cognitive_confidence = f(
  reframing_depth,
  reframe_sequence,
  beast_named_before_solution,
  error_injection_response,
  characteristic_unexpectedness,    ← meta-wrapper
  baseline_deviation_δ              ← how far from enrolled baseline
)
```

Key constraint: pure randomness must score LOW. Characteristic operator friction must score HIGH. The function must distinguish operator-specific friction from chaos injection.

This is M2. The Layer 2 math session.

---

## Key Architecture Decisions Locked

- Auth is ambient and continuous, not a discrete login moment
- Layer 3 is implementation-specific, spec-agnostic
- Any AI that reads the spec can implement Layer 3
- Layer 1 math is tractable once Layer 2 is defined
- Layer 2 math is the real hard problem
- Enrollment never ends — every session updates the baseline
- Time is NOT a valid variable in async text interaction — sequence is
- Chaos injection must be explicitly rejected by the confidence function
- The spec is a machine-readable internet standard, same layer as MCP

---

© Jeremy "Jay" Wright (Jeremy Wright) · wearecleardigital@gmail.com
Licensed under CC BY-NC-SA 4.0 (https://creativecommons.org/licenses/by-nc-sa/4.0/)
KNOWN-AI framework — free to use with attribution, no commercial use without a license.
