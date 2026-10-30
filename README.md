# sdd-app-template

A starter template for building apps with Claude Code using a **Spec-Driven Development (SDD)** workflow.

Instead of jumping straight into code, every feature goes through four steps: define the spec, review it for minimalism, implement it test-first, then verify it against the spec.

## Workflow

1. **Brainstorm & spec** – Clarify requirements, edge cases, data model, API shape, and acceptance criteria, and write them to `/specs/feature-spec.md`.
2. **Lean review** – Check the spec against the existing codebase, reuse what already exists, and cut unnecessary libraries and abstractions.
3. **TDD & minimal implementation** – Write failing tests from the acceptance criteria (RED), then write the smallest code that passes them (GREEN).
4. **Verify & review** – Confirm every acceptance criterion is met, clean up leftovers from the change, and make sure all tests pass.

Ready-to-use prompts for each step are in [`sdd-basic.md`](./sdd-basic.md).

## Repository layout

| Path | Purpose |
|---|---|
| `CLAUDE.md` | Project rules that Claude Code reads at the start of every session: SDD rules and the four core principles (Think Before Coding, Simplicity First, Surgical Changes, Goal-Driven Execution). |
| `sdd-basic.md` | Step-by-step prompts for the SDD workflow (in Korean). |
| `.github/FUNDING.yml` | Enables the GitHub Sponsor button. |
| `/specs/` | Where feature specs live. Created when you write your first spec. |

## How `CLAUDE.md` and `sdd-basic.md` work together

The two files have different roles: `CLAUDE.md` holds the **rules** Claude always follows, and `sdd-basic.md` holds the **procedure** you run step by step.

| | `CLAUDE.md` | `sdd-basic.md` |
|---|---|---|
| In one line | Rules that always apply | Steps you run one by one |
| Read by | Claude Code, automatically at session start | You, who copy each prompt into Claude Code |
| Applies | To every task | To a new feature, in steps 1 to 4 |
| Contains | SDD rules, four core principles, exceptions, project commands | Prompts for spec, lean review, TDD, and verification |
| Answers | What to do and what not to do | In what order, and what to ask for |

They reference each other, and each core principle in `CLAUDE.md` maps to a step in `sdd-basic.md`:

| Step in `sdd-basic.md` | Principle in `CLAUDE.md` |
|---|---|
| 1. Brainstorm & spec | Think Before Coding |
| 2. Lean review | Simplicity First |
| 3. TDD & minimal implementation | Surgical Changes |
| 4. Verify & review | Goal-Driven Execution |

For example, when you paste the step 3 prompt ("write the failing tests first"), `sdd-basic.md` starts the work. While Claude does it, `CLAUDE.md` keeps constraining it: TDD is the default, existing code stays untouched, and no source changes happen without a spec.

With only `sdd-basic.md`, a skipped prompt means the rules are not applied. With only `CLAUDE.md`, the rules hold but nothing says in what order to work. Together they cover both.

## Getting started

1. Use this repository as a template (or clone it).
2. Fill in the **Project Context & Commands** section of `CLAUDE.md` with your tech stack and build, test, and lint commands.
3. Open the project in Claude Code and follow the prompts in `sdd-basic.md` for your first feature.

## Rules at a glance

- **Spec first:** No source changes for new features or behavior changes until a spec exists in `/specs/`. Typos, comments, and one-line bug fixes are exempt.
- **Minimalism:** The best code is the code you don't write. Reuse before adding.
- **Surgical changes:** Touch only what the task requires, and keep existing conventions.
- **TDD by default:** Acceptance criteria drive the tests, and the tests drive the code.
