# NeuroLens Architecture

## Purpose

NeuroLens is intended to become a screen-aware assistant that can convert raw
workspace activity into useful, context-sensitive guidance.

The architecture is designed to answer five questions repeatedly:

1. What is happening on the screen?
2. What task is the user likely working on?
3. What matters right now?
4. What has happened before that is relevant?
5. What should be suggested, deferred, or automated next?

## System Overview

The planned system has six major layers:

| Layer | Responsibility | Possible implementation paths |
| --- | --- | --- |
| Capture | Acquire screen frames and window metadata | OS APIs, `mss`, event hooks |
| Perception | Extract text, UI structure, and visible entities | OCR, vision models, heuristics |
| Context | Build a structured representation of user state | task graph, session state, app metadata |
| Reasoning | Interpret context and generate suggestions | LLMs, rules, planners |
| Memory | Store recent and long-term patterns | cache, vector store, structured logs |
| Feedback / Action | Present insight or trigger controlled automation | overlay, notifications, scripts |

## Layer Breakdown

### 1. Capture

The capture layer is responsible for collecting the minimum data required to
understand what the user is doing. It may include:

- screen frames,
- active window information,
- timestamps,
- app switches,
- optional keyboard or pointer summaries.

The capture layer should be designed to support selective sampling rather than
constant high-frequency recording.

### 2. Perception

The perception layer converts raw visual input into structured signals such as:

- visible text,
- application identity,
- document or code context,
- repeated interface patterns,
- notable UI events.

This layer may combine OCR, image understanding, and deterministic heuristics.
Its output should be normalized into machine-readable events rather than passed
forward as raw screenshots.

### 3. Context Builder

The context builder merges current observations with recent history to answer:

- what task is underway,
- what subtask the user is in,
- what resource they are interacting with,
- whether they are progressing or thrashing,
- whether they have switched context recently.

This is the translation layer between perception and reasoning.

### 4. Reasoning Engine

The reasoning layer consumes structured context and determines what to do next.
Possible outputs include:

- a suggestion,
- a clarification prompt,
- a warning about waste or distraction,
- a candidate automation,
- no intervention at all.

This layer should be conservative. Irrelevant guidance is worse than silence.

### 5. Memory

The memory layer is split into two scopes:

- short-term memory for active session continuity,
- long-term memory for recurring patterns, preferences, and repeated workflows.

Memory should support retrieval that is explainable and bounded. The system
must avoid opaque behavior driven by irrelevant historical context.

### 6. Feedback and Action

The final layer exposes the output to the user. The default modes are:

- lightweight feedback,
- optional workflow suggestions,
- explicit approval before automation.

The system should not silently perform high-impact actions.

## Canonical Data Flow

1. Capture a frame or event.
2. Extract OCR and visual signals.
3. Normalize output into structured context.
4. Merge with short-term history.
5. Retrieve relevant memory if needed.
6. Generate a recommendation or action proposal.
7. Present the result through a safe interface.

## Architectural Constraints

- Privacy: sensitive screen content must be handled carefully and minimized.
- Latency: the loop must be fast enough to remain relevant.
- Accuracy: false interpretations can erode trust quickly.
- Explainability: the user should understand why a suggestion appears.
- Modularity: each layer should be replaceable without rewriting the whole
  stack.

## Risks and Failure Modes

- OCR noise leading to incorrect task inference.
- Excessive capture frequency increasing cost and privacy risk.
- Suggestions that interrupt rather than assist.
- Long-term memory surfacing irrelevant or stale context.
- Automation executing without sufficient user intent or confidence.

## Current State

This architecture is a working design target, not a finished implementation.
The next step is to validate the narrowest useful version of the loop through a
small prototype and staged experiments.
