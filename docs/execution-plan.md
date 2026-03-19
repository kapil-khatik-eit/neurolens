# NeuroLens Execution Plan

## Goal

Build NeuroLens in stages, starting from a narrow prototype and expanding only
when the earlier layers are reliable enough to justify the next one.

This plan favors incremental validation over broad initial scope.

## Phase 0: Public Foundation

Objective: publish a clear and credible project foundation.

Deliverables:

- an authoritative `README.md`,
- an architecture document,
- an execution plan,
- a clean repository layout for future work.

Exit criteria:

- a new visitor can understand the idea, scope, and intended build path within
  a few minutes,
- there is no conflicting or duplicated documentation in the repository.

## Phase 1: Capture and OCR Prototype

Objective: prove that screen content can be sampled and converted into useful
text or event signals.

Deliverables:

- constrained screen capture,
- OCR extraction on selected regions or windows,
- timestamped output suitable for downstream processing.

Questions to answer:

- what sampling rate is useful without being intrusive,
- how reliable is OCR across terminals, editors, and browsers,
- what metadata is needed in addition to raw text.

## Phase 2: Context Builder

Objective: transform low-level observations into structured task state.

Deliverables:

- event schema,
- session history handling,
- heuristic or model-assisted task classification,
- context snapshots that can be passed into a reasoning layer.

Questions to answer:

- what is the smallest context representation that is still useful,
- how should task switching and ambiguity be represented,
- what confidence signals are needed.

## Phase 3: Reasoning and Memory

Objective: generate recommendations based on present context and relevant past
activity.

Deliverables:

- prompt and policy design,
- retrieval strategy for recent and long-term memory,
- recommendation formatting with confidence and rationale.

Questions to answer:

- when should the system stay silent,
- what memory retrieval strategy improves relevance,
- how should unsafe or low-confidence suggestions be suppressed.

## Phase 4: Feedback and Controlled Action

Objective: deliver insight in a user-friendly way and explore limited
automation.

Deliverables:

- a lightweight feedback surface,
- explicit approval flow for actions,
- instrumentation to measure usefulness and interruption cost.

Questions to answer:

- which interface is least disruptive,
- which actions are safe enough to automate,
- how should consent and reversibility be handled.

## Phase 5: Evaluation and Hardening

Objective: determine whether the system is genuinely useful and safe to expand.

Deliverables:

- latency measurements,
- suggestion quality review,
- privacy review,
- failure-mode tracking,
- milestone decision for wider implementation.

Success criteria:

- the system produces relevant guidance often enough to justify continued work,
- privacy and control constraints remain acceptable,
- each layer can be improved without destabilizing the whole system.

## Cross-Cutting Workstreams

The following concerns should be addressed throughout all phases:

- privacy and consent,
- observability and logging,
- evaluation methodology,
- modular interfaces between layers,
- documentation quality.

## Near-Term Priorities

For the next repository iteration, the practical priorities are:

1. keep the public documentation current,
2. define the first prototype boundaries,
3. add implementation only when it is narrow, testable, and well-scoped.
