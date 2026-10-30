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

## Example: starting a project

Below is a walkthrough with a small to-do app. Replace the app idea with your own. The prompts in `sdd-basic.md` are in Korean, and you can write yours in any language.

**0. Set up the project context**

```text
This is a new project built from this template. I want a to-do web app
with TypeScript, React, and Vite, tested with Vitest.
Scaffold the minimum project setup, then fill in the "Project Context & Commands"
section of CLAUDE.md with the real tech stack and build, test, and lint commands.
Do not add any feature code yet.
```

**1. Brainstorm & spec**

```text
Apply the Brainstorming approach from sdd-basic.md.
The feature I want: "Users can add, complete, and delete to-do items.
Items persist in the browser between visits."

1. Do not write code yet. Ask me 3 to 5 questions about edge cases, the data model,
   and acceptance criteria.
2. Once I answer, write the requirements and details to /specs/feature-spec.md.
```

**2. Lean review**

```text
Read /specs/feature-spec.md and the current codebase.
Apply the minimalism principle: reuse existing code, remove unneeded libraries
and abstractions, and simplify the plan.
Update the [Implementation Plan] section of the spec with the leanest plan.
```

**3. TDD & minimal implementation**

```text
Implement the [Implementation Plan] in /specs/feature-spec.md.

1. RED: write failing tests that check each acceptance criterion.
2. GREEN: write only the minimum code that makes them pass.
3. Run the tests and show me they pass.
```

**4. Verify & review**

```text
The implementation is done. Verify it against /specs/feature-spec.md.

1. Show a checklist of every acceptance criterion and whether it is met.
2. Clean up leftovers from this change only: debug comments, unused variables,
   duplicated logic.
3. Run all tests and summarize the result.
```

For the next feature, repeat steps 1 to 4 with a new spec file. `CLAUDE.md` keeps applying the rules in every step, so you do not need to repeat them in the prompts.

## Rules at a glance

- **Spec first:** No source changes for new features or behavior changes until a spec exists in `/specs/`. Typos, comments, and one-line bug fixes are exempt.
- **Minimalism:** The best code is the code you don't write. Reuse before adding.
- **Surgical changes:** Touch only what the task requires, and keep existing conventions.
- **TDD by default:** Acceptance criteria drive the tests, and the tests drive the code.
