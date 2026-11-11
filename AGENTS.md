# AGENTS.md

This repository holds a Home Assistant automation blueprint for Ring Intercoms. It unlocks the door only while a helper `input_boolean` (the gate) is on. The behaviour is described in the [README](README.md).

## Layout

| Path | What |
|---|---|
| `automation/ring_intercom/ring_to_open.yaml` | The blueprint |
| `README.md` | Scenarios, configuration and safety guarantees |

There is no build or test command. Changes must keep the "Safety Guarantees" listed in the README, above all: no unlock without the gate.

## Pull requests

- Branch off `main` with `feat/`, `fix/`, `docs/`, `chore/` or `refactor/`, and open the PR against `main`.
- Write the PR title as a Conventional Commit (`fix(blueprint): …`). PRs are squash-merged, so the title becomes the commit message.
- Start the PR body with the issue line: `Closes #N`, `Refs #N` or `No issue: <reason>`.
- Direct pushes to `main` are blocked by the repository ruleset and the global pre-push hook. Merge only when the checks are green.
- This repository is public. Use made-up entity names such as `input_boolean.ring_to_open`, never real devices, people or addresses.

## Code Review Rules

- Review for correctness and security only. No style comments.
- Skip generated files and lockfiles.
