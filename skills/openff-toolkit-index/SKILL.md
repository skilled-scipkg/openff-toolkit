---
name: openff-toolkit-index
description: This skill should be used when users ask how to use openff-toolkit and the correct generated documentation skill must be selected before going deeper into source code.
---

# openff-toolkit Skills Index

## Route the request
- Classify the request into one of the generated topic skills listed below.
- Prefer abstract, workflow-level guidance for large scientific packages; do not attempt full function-by-function coverage unless explicitly requested.

## Generated topic skills
- `openff-toolkit-build-and-install`: Build and Install (environment setup, installation paths, optional toolkit dependencies)
- `openff-toolkit-inputs-and-modeling`: Inputs and Modeling (SMIRNOFF/OFFXML parameterization workflows and model setup)
- `openff-toolkit-users`: Users (core concepts, conversion behavior, virtual-site semantics)
- `openff-toolkit-api-and-scripting`: API and Scripting (toolkit wrappers, registries, version-aware scripting)
- `openff-toolkit-examples-and-tutorials`: Examples and Tutorials (runnable notebooks/scripts and validated workflow recipes)
- `openff-toolkit-templates`: Templates (Sphinx autosummary template behavior for API docs)
- `openff-toolkit-advanced-topics`: Advanced Topics (developer guide, simulation-workflow single-doc topic, topology and utility references)

## Documentation-first inputs
- `docs`

## Tutorials and examples roots
- `examples`

## Test roots for behavior checks
- `openff/toolkit/_tests`

## Escalate only when needed
- Start from topic skill primary references.
- If those references are insufficient, open `skills/<topic-skill>/references/doc_map.md`.
- If documentation still leaves ambiguity, open `skills/<topic-skill>/references/source_map.md` and inspect the suggested source entry points.
- Use targeted symbol search while inspecting source (e.g., `rg -n "<symbol_or_keyword>" openff/toolkit`).

## Source directories for deeper inspection
- `openff/toolkit`
