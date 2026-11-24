---
title: "레슨 3 - 에이전트 모드: Plan 및 Autopilot"
description: "Plan으로 접근 방식을 합의하고, Autopilot으로 이슈의 필터링을 구현하고, Interactive 모드로 결과를 검토합니다."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

먼저 프로젝트에 작은 기능을 추가했습니다. 하지만 큰 변경에는 더 견고한 프로세스가 필요합니다. GitHub Copilot CLI는 조직의 기존 워크플로와 함께 사용하도록 설계되어 올바른 것을 올바른 방식으로 만들 수 있습니다. 이 레슨부터 여러 개의 레슨에서 일반적인 에이전트 기반 개발 프로세스를 따라갑니다. 이슈를 사용해 새 기능을 생성하고 코드를 검증하고 기능이 예상대로 동작하는지 확인한 다음 프로젝트에 성공적으로 병합합니다.

> [!NOTE]
> 기능 워크플로를 계속 진행하면서 같은 대화와 브랜치를 사용합니다. 일반적으로는 작업하는 파일 유형별로 서로 다른 브랜치나 PR을 사용하지만, 여기서는 핵심 개념에 집중하기 위해 단축한 방법을 사용합니다.

이 레슨에서는 다음을 수행합니다.

- GitHub 이슈에서 새 Copilot 대화를 시작합니다.
- Plan 모드에서 요구 사항을 정의합니다.
- Autopilot 모드로 새 기능을 구현합니다.
- 코드를 검토합니다.
- 전달된 브라우저에서 기능을 수동으로 검증합니다.

이 기능을 계속 구현하면서 리포지토리 지침을 업데이트하고 기존 `quality-checks` 스킬을 사용자 지정하며 MCP 검증을 추가하고 QA 에이전트를 만들고 기능 PR을 엽니다.

## 시나리오

Tailspin Toys의 카탈로그가 커지면서 방문자는 카테고리와 게시자로 게임을 좁혀 볼 수 있어야 합니다. 백로그 이슈에는 기능이 설명되어 있지만 카테고리 결합 같은 세부 사항은 코딩 전에 합의가 필요합니다. Plan 모드로 결정 사항을 해결한 다음 Autopilot으로 범위가 제한된 구현을 승인합니다.

## 배경

AI 코딩 에이전트를 개발 흐름에 도입해도 기본 원칙은 바뀌지 않습니다. 오히려 기본 원칙이 더 중요해집니다. 대부분의 개발자는 다음과 같은 흐름을 따릅니다.

1. 수행할 작업을 설명하는 등록된 이슈에서 시작합니다.
2. 구현할 내용을 계획합니다.
3. 코드를 빌드하고 검토합니다.
4. 테스트를 실행하여 코드를 검증합니다.
5. 새 기능을 수동으로 검증합니다.
6. 풀 리퀘스트(PR)를 만듭니다.
7. 코드가 검토되고 지속적 통합 프로세스가 성공하면 코드를 병합합니다.

> [!NOTE]
> 팀과 조직에 따라 구체적인 절차는 달라질 수 있습니다. 하지만 대부분 위에 표시된 흐름의 변형입니다.

이 표준 접근 방식을 따르면 AI가 생성한 코드가 요구 사항을 충족하고 사람이 직접 작성한 코드와 같은 검토 프로세스를 거치게 할 수 있습니다.

## 대화 모드

**대화 모드**는 에이전트에 부여되는 자율성의 수준을 결정합니다. <kbd>Shift</kbd>+<kbd>Tab</kbd>을 눌러 모드를 순환합니다.

- **Interactive**: 사용자와 에이전트가 함께 작업합니다. 에이전트가 변경을 제안하고 진행하기 전에 사용자 입력을 기다립니다.
- **Plan**: 에이전트가 먼저 계획을 만들고 프로젝트 파일 편집을 차단합니다.
- **Autopilot**: 에이전트가 코드를 작성하고 테스트를 실행하며 작업이 완료될 때까지 반복하여 자율적으로 작업합니다.

Plan 모드로 시작해 계획을 검토한 다음 Autopilot으로 구현합니다.

## 이슈에서 시작하기

필터링 작업을 시작하기 전에 Codespace로 돌아가 리포지토리와 터미널이 준비되었는지 확인합니다.

1. Codespace로 돌아갑니다. 중지되어 있으면 계속하기 전에 다시 시작합니다.
2. 별점 PR이 병합되었는지 확인합니다.
3. 터미널이 열려 있지 않으면 <kbd>Control</kbd>+<kbd>\`</kbd>(Mac) 또는 <kbd>Ctrl</kbd>+<kbd>\`</kbd>(Windows/Linux)를 누릅니다.
4. `main`을 업데이트한 다음 필터링 작업용 브랜치를 만듭니다.

   ```bash
   git checkout main
   git pull --ff-only
   git checkout -b game-filters-cli
   ```

5. Copilot CLI를 시작합니다.

   ```bash
   copilot --yolo
   ```

6. <kbd>Tab</kbd>을 두 번 눌러 **Issues** 탭을 엽니다.
7. <kbd>A</kbd>를 눌러 모든 이슈를 표시합니다.
8. 화살표 키로 **Allow users to filter games by category and publisher** 제목의 이슈를 선택합니다.
9. <kbd>C</kbd>를 눌러 이슈를 프롬프트에 추가하고 **Session** 탭으로 돌아갑니다.

이제 프롬프트가 `#7` 또는 유사한 번호로 시작하는 것을 확인할 수 있습니다. `#`를 사용하면 GitHub의 이슈나 풀 리퀘스트(PR)를 컨텍스트로 가져올 수 있습니다.

## 필터링 기능 계획하기

계획을 세우면 Copilot에 작업을 넘기기 전에 기능 구현 또는 작업 수행 방법을 정의할 수 있습니다. 복잡한 작업이라면 계획에 시간을 쓰는 것이 좋습니다. Plan 모드로 전환하여 Copilot에게 계획을 만들도록 요청합니다.

1. <kbd>Shift</kbd>+<kbd>Tab</kbd>을 눌러 Plan 모드로 전환합니다. 프롬프트 아래의 모드 표시기에 **Plan**이 표시되는지 확인합니다.
2. 이전 단계에서 추가한 이슈 참조 다음에 다음 프롬프트를 입력합니다.

   ```plaintext
   Create a plan for implementing this feature.
   ```

Copilot이 계획을 작성합니다. 먼저 프로젝트를 탐색한 다음 최상의 접근 방식을 결정합니다.

3. 계획을 세우는 동안 Copilot이 필터링 기능의 동작에 대해 질문할 수 있습니다. 선호하는 대로 답변합니다. 정답은 없습니다.
4. 계획이 완성되면 <kbd>Control</kbd>+<kbd>E</kbd>(Mac) 또는 <kbd>Ctrl</kbd>+<kbd>E</kbd>(Windows/Linux)를 눌러 계획을 확장합니다.
5. 위아래로 스크롤하여 계획을 검토합니다.
6. 결정 사항과 맞지 않는 계획 부분은 Copilot에게 수정하도록 요청합니다.

## Autopilot 승인

계획을 작성하고 검토했으니 구현할 차례입니다. Autopilot을 사용하여 Copilot이 작업을 수행하도록 합니다.

Autopilot을 사용하면 Copilot이 작업이 완료되었다고 판단할 때까지 문제를 반복적으로 해결합니다.

1. **Accept plan and build on autopilot (recommended)** 또는 설치된 버전에 표시되는 유사한 옵션을 선택합니다.
2. 프롬프트 아래의 모드 표시기에 **Autopilot**이 표시되는지 확인합니다.
3. Copilot이 계획을 따라 반복하고 코드를 생성하며 테스트를 실행하는 모습을 확인합니다.

> [!NOTE]
> 승인이 즉시 구현을 시작할 수 있으므로 먼저 계획을 검토합니다. Copilot이 누락된 종속성이나 포트 충돌을 보고하면 검사 완료로 판단하기 전에 설정 문제를 해결합니다.

## 구현 검토 및 검증

코드가 생성되면 다른 코드와 마찬가지로 병합 전에 검토해야 합니다. 코드를 검토하고 사이트를 실행하여 모든 것이 올바르게 동작하는지 확인합니다.

1. <kbd>Shift</kbd>+<kbd>Tab</kbd>을 눌러 Interactive 모드로 전환합니다. 모드 표시기에 **Plan**이나 **Autopilot**이 더 이상 표시되지 않는지 확인합니다.
2. `/diff`를 입력하고 필터링 구현과 테스트를 검사합니다.
3. 결과를 이슈와 계획 단계에서 내린 결정과 비교합니다.
4. 코드 검토를 마쳤으면 <kbd>Esc</kbd>를 눌러 diff 보기에서 종료합니다.
5. 프로젝트 검사 결과를 검토하고 실패가 있으면 Copilot에게 해결하도록 요청합니다.

## 새 기능 살펴보기

코드는 괜찮아 보입니다. 하지만 실제로 실행됩니까? 이전과 같이 앱을 시작하고 Codespaces 전달 포트를 통해 사이트를 엽니다.

1. Copilot에 앱을 시작하도록 요청합니다.

   ```plaintext
   Start the app so I can try the filtering feature in my browser. Tell me the URL and leave the server running.
   ```

2. Codespaces에서 포트 `4321`을 사용할 수 있다고 표시되면 **Open in Browser**를 선택합니다.
3. 계획에서 합의한 카테고리 필터링, 게시자 필터링 및 조합을 시험합니다.
4. 재설정 및 빈 결과 동작이 이슈와 결정과 일치하는지 확인합니다.
5. Codespace로 돌아가 Copilot에게 시작한 개발 서버를 중지하도록 요청합니다.

## 요약 및 다음 단계

다양한 대화 모드를 사용해 기능을 구현하고 검토했습니다. 이 레슨에서는 다음을 수행했습니다.

- GitHub 이슈에서 새 Copilot 대화를 시작했습니다.
- Plan 모드에서 요구 사항을 정의했습니다.
- Autopilot 모드로 새 기능을 구현했습니다.
- 코드를 검토했습니다.
- 전달된 브라우저에서 기능을 수동으로 검증했습니다.

다음으로 [사용자 지정 지침 사용][next-lesson]을 통해 코드가 문서화된 관행을 따르는지 더 깊이 살펴봅니다.

## 리소스

- [GitHub Copilot CLI의 Autopilot][autopilot]
- [Copilot CLI 명령 참조][cli-reference]

[autopilot]: https://docs.github.com/copilot/concepts/agents/copilot-cli/autopilot
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[previous-lesson]: ../2-add-star-rating/
[next-lesson]: ../4-custom-instructions/
