Superpowers와 Ponytail의 철학을 실제 Claude Code 환경에서 단계별로 따라 할 수 있는 프롬프트 모음입니다.
새로운 기능을 개발할 때, 아래 단계에 맞춰 프롬프트를 Claude Code에 차례대로 입력하세요.
0단계: 환경 점검 (프로젝트당 1회)
> 목적: 이 템플릿이 활용하는 Superpowers, Ponytail, `/code-review`가 있는지 확인하고, 없으면 설치 방법을 안내받는 단계입니다. 모두 있으면 바로 1단계로 가세요. 스킬 없이도 1~4단계 프롬프트는 동작하지만, 설치하면 더 정교하게 적용됩니다.
> 
[단계 0: 환경 점검]
이 템플릿은 Superpowers, Ponytail 스킬과 `/code-review`를 활용해. 아래를 점검해줘.

1. 현재 사용 가능한 스킬/플러그인 목록에서 Superpowers, Ponytail, `code-review`가 있는지 확인해줘. Ponytail 훅은 Node.js가 필요하니 `node --version`도 확인해줘.
2. 항목별 있음/없음을 표로 보여줘.
3. 없는 항목은 직접 설치하지 말고 아래 명령만 안내해줘. 설치는 내가 직접 실행할게.
   - Superpowers: `/plugin marketplace add obra/superpowers-marketplace` 후 `/plugin install superpowers@superpowers-marketplace`
   - Ponytail: `/plugin marketplace add DietrichGebert/ponytail` 후 `/plugin install ponytail@ponytail` (포크가 많으니 DietrichGebert 저장소인지 확인)
   - `code-review`: 설치 대상이 아니야. 없으면 4단계의 선택 항목은 건너뛰어줘.
4. 설치 후 새 세션에서 이 점검을 다시 실행해 확인할 수 있게 안내해줘.

> 설치 명령은 각 저장소 README에서 최신 여부를 한 번 확인하세요.

1단계: 브레인스토밍 및 스펙 문서 작성
> 목적: 바로 코딩하지 않고 요구사항을 명확히 정의하여 /specs/에 스펙 문서를 만드는 단계입니다.
> 
[단계 1: 브레인스토밍 및 스펙 정의]
Superpowers의 Brainstorming 방식을 적용해줘.
내가 구현하려는 기능은 다음과 같아:
"[여기에 개발하려는 기능/요구사항 작성]"

1. 바로 코드를 작성하지 말고, 내가 놓친 예외 상황(Edge Cases), 데이터 모델, API 구조, 수락 기준(Acceptance Criteria)에 대해 필요한 질문을 3~5개만 던져줘.
2. 내 답변을 바탕으로 `/specs/feature-spec.md` 파일에 요구사항 및 상세 명세를 작성해줘.

2단계: Ponytail 기반 미니멀 설계 검토
> 목적: 불필요한 라이브러리 추가나 오버엔지니어링을 제거하여 스펙과 계획을 최소화하는 단계입니다.
> 
[단계 2: Ponytail Lean 검토]
작성된 `/specs/feature-spec.md`와 현재 프로젝트의 코드베이스를 분석해줘.
Ponytail의 철학("최고의 코드는 작성하지 않은 코드다")을 적용해서 다음 사항을 점검해줘:

1. 기존 프로젝트 코드 중 재사용할 수 있는 모듈/함수가 있는가?
2. 새로 설치하거나 작성하려는 라이브러리/클래스 중 불필요한 것이 있는가?
3. 최소한의 코드 수정만으로 이 명세를 만족할 수 있도록 구현 계획(Plan)을 단순화하여 `/specs/feature-spec.md`의 [Implementation Plan] 섹션에 업데이트해줘.

3단계: TDD 기반 최소 코드 구현
> 목적: 명세서의 수락 기준을 충족하는 테스트를 먼저 만들고, 테스트를 통과하는 최소한의 코드를 작성하는 단계입니다.
> 
[단계 3: TDD 및 최소 구현]
이제 `/specs/feature-spec.md`에 정의된 [Implementation Plan]을 바탕으로 개발을 진행해줘.

1. (RED) 명세서의 수락 기준(Acceptance Criteria)을 검증하는 실패하는 테스트 코드를 먼저 작성해줘.
2. (GREEN) 테스트를 통과시키는 데 **필요한 가장 최소한의 코드만** 작성해줘. 불필요한 추상화나 미래를 대비한 과도한 코드는 절대 작성하지 마.
3. 테스트를 실행하여 정상 통과하는지 확인해줘.

4단계: 스펙 검증 및 리팩토링 리뷰
> 목적: 코드가 명세(Spec)에서 벗어나지 않았는지 검증하고, 군더더기 없는 상태로 마무리하는 단계입니다.
> 
[단계 4: 검증 및 최종 리뷰]
구현이 완료되었어. Superpowers의 Review 및 Ponytail의 검수 기준을 적용해서 최종 검증을 진행해줘.

1. 작성된 코드와 테스트가 `/specs/feature-spec.md`의 모든 수락 기준을 100% 충족하는지 체크리스트로 보여줘.
2. 디버깅용 주석, 사용하지 않는 변수, 중복 로직이 남아있지 않은지 점검하고 정리해줘.
3. 모든 테스트가 통과하는지 최종 확인 후 완료 보고서를 요약해줘.
4. (선택) `/code-review`로 이번 diff의 버그를 점검해줘. 수정은 적용하지 말고 보고만 해줘.

💡 팁: 세션 시작 시 적용되는 개발 규칙은 루트의 `CLAUDE.md`를 참고하세요.
