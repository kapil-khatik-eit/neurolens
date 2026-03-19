# NeuroLens

NeuroLens is a public research and planning repository for a screen-aware AI
assistant that can observe digital workflows, build context, and provide
practical guidance for improving focus, execution, and decision-making.

This repository is intended to document the idea clearly, explain the system
design, and share the execution plan for building it in public.

## Status

NeuroLens is in the planning stage.

- The repository currently contains architecture and execution documents.
- No production-ready implementation is committed yet.
- The goal of the initial public commit is clarity, not feature completeness.

## Why This Project Exists

Modern knowledge work is fragmented across editors, terminals, browsers,
documents, dashboards, and communication tools. Valuable context is spread
across those surfaces, which makes it difficult to:

- understand what a user is trying to achieve,
- detect wasted motion or context switching,
- surface better next actions at the right moment,
- build a durable memory of workflows and patterns.

NeuroLens is an attempt to design a system that can:

- observe the active workspace,
- interpret what is happening,
- reason about the current task,
- retrieve useful historical context,
- suggest or trigger the next best action.

## Core Idea

At a high level, the system is designed around this loop:

Capture -> Perception -> Context -> Reasoning -> Memory -> Feedback / Action

The intended behavior is not passive surveillance. The target is a
human-in-the-loop assistant that helps users work more deliberately and with
less friction.

![NeuroLens architecture](docs/architecture.svg)

## Repository Scope

This repository is the public foundation for the project. It is meant to hold:

- the problem framing,
- the architecture,
- the execution roadmap,
- research questions and constraints,
- future implementation milestones.

It is not yet intended to present a finished product or a stable SDK.

## Documentation

- [Architecture](docs/architecture.md)
- [Execution plan](docs/execution-plan.md)

## Design Principles

- Local-first by default where feasible.
- Privacy-aware handling of screen and behavioral data.
- Human oversight before any meaningful automation.
- Modular layers so capture, perception, reasoning, memory, and feedback can
  evolve independently.
- Measurable progress through staged milestones instead of broad claims.

## Initial Roadmap

1. Define the system architecture and repository foundation.
2. Build a narrow capture and OCR prototype.
3. Introduce a context builder that converts raw observations into structured
   task state.
4. Add reasoning and memory layers for suggestions and workflow recall.
5. Evaluate usefulness, latency, privacy posture, and failure modes before any
   broader automation.

The detailed build sequence lives in [docs/execution-plan.md](docs/execution-plan.md).

## Current Repository Layout

```text
.
|-- README.md
|-- LICENSE
|-- docs/
|   |-- architecture.md
|   |-- architecture.svg
|   `-- execution-plan.md
`-- .gitignore
```

## What Is Not Included Yet

- production code,
- packaged libraries,
- benchmark results,
- deployment instructions,
- user-facing applications.

Those will be added only when the implementation reaches a level worth
publishing.

## Contributing

Early feedback is useful. Issues and discussions should focus on:

- architecture quality,
- research blind spots,
- privacy and safety risks,
- milestone sequencing,
- evaluation methodology.

## License

This repository is licensed under the MIT License. See [LICENSE](LICENSE).
