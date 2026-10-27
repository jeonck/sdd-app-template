# Claude Code Project Guidelines

## Development Rules (SDD)

- **Process:** Superpowers(Brainstorming -> Plan -> TDD -> Review) 스킬 흐름을 준수한다. 단계별 프롬프트는 `sdd-basic.md` 참고.
- **Philosophy:** Ponytail(Minimalism) 철학을 적용하여 오버엔지니어링을 방지하고 불필요한 코드를 추가하지 않는다.
- **Spec First:** `/specs/` 폴더 내에 명세서가 작성 및 검토되기 전에는 소스 코드를 직접 수정하지 않는다.
  - 신규 기능과 동작 변경에 적용한다. 오타·주석·한 줄 버그 수정은 예외로 스펙 없이 진행한다.

## Core Principles

1. **Think Before Coding** (브레인스토밍·스펙 단계)
   - Don't guess or assume requirements. If something is ambiguous, trade-offs exist, or context is missing, ask for clarification.
   - Plan out complex changes before writing code. Outline your approach step-by-step.

2. **Simplicity First** (Ponytail 검토 단계)
   - Avoid over-engineering, unnecessary abstractions, or future-proofing for hypothetical needs.
   - Write the simplest code that completely solves the current problem.
   - Prefer concise, readable solutions (e.g., 50 clear lines over 200 lines of complex framework abstractions).
   - 최소 코드 원칙은 소스 코드에 적용한다. 수락 기준을 검증하는 테스트 코드는 줄이지 않는다.

3. **Surgical Changes** (TDD 구현 단계)
   - Only modify what was explicitly requested or strictly necessary for the fix.
   - Do not touch unrelated files, refactor working code unnecessarily, or change code formatting style across the repository.
   - Preserve existing code conventions and patterns.
   - 단계 4의 정리(미사용 변수, 중복 로직, 디버깅 주석)는 이번 변경이 만든 코드에 한정한다. 기존 코드는 건드리지 않는다.

4. **Goal-Driven Execution** (검증·리뷰 단계)
   - Set clear, verifiable success criteria before executing tasks. In this repo, the criteria are the Acceptance Criteria in `/specs/`.
   - Verify changes after implementation through tests, dry-runs, or manual verification steps.
   - 이 리포에서는 TDD(RED -> GREEN)가 기본이다. 수동 검증은 테스트로 검증할 수 없을 때만 보조로 사용한다.
   - Ensure the solution genuinely works as expected before declaring completion.

---

## Project Context & Commands

- **Tech Stack:** TBD
- **Build Command:** TBD
- **Test Command:** TBD
- **Lint Command:** TBD

> Note: 앱 스택이 정해지면 위 항목을 실제 값으로 갱신한다.
