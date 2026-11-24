---
title: "레슨 2 - 별점 추가: 빠른 성과"
description: "Copilot CLI를 사용해 게임 카드의 작은 변경을 수행하고, 전달된 브라우저에서 검토한 뒤 첫 풀 리퀘스트로 병합합니다."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

Copilot CLI를 설치하고 대화를 시험해 봤으니 이제 프로젝트에 첫 변경을 수행할 차례입니다. 변경 범위는 작게 유지합니다. 게임 데이터에는 이미 별점이 있지만 홈 페이지의 게임 카드에는 아직 별점이 표시되지 않습니다. 에이전트에게 별점을 표시하고 변경 사항을 검토한 뒤 첫 풀 리퀘스트(PR)로 병합하도록 요청합니다.

이 레슨에서는 다음을 수행합니다.

- 기능 브랜치에서 집중된 Copilot 대화를 시작합니다.
- 에이전트에게 프로젝트의 작은 변경을 요청합니다.
- `/diff`로 변경 사항을 검토합니다.
- 전달된 브라우저에서 앱을 실행하여 변경 사항을 확인합니다.
- 첫 풀 리퀘스트를 열고 병합합니다.

## 시나리오

Tailspin Toys의 각 게임에는 별점이 있을 수 있으며 게임 상세 페이지에는 이미 별점이 표시됩니다. 하지만 홈 페이지의 게임 카드에는 제목, 카테고리, 게시자, 설명만 표시됩니다. 준비 운동으로 에이전트가 각 카드에 기존 별점을 표시하도록 합니다. 이는 첫 세션에 적합한 작고 독립적인 변경입니다.

## 대화의 구조

**대화**는 Copilot CLI로 작업을 수행하는 곳입니다. Copilot 앱과 달리 일반 CLI 대화는 전용 작업 트리를 만들지 않고 터미널에서 현재 체크아웃된 리포지토리와 Git 브랜치를 사용합니다. 저장된 대화에서는 나중에 같은 대화로 돌아갈 수 있지만, 파일과 브랜치는 디스크에 있는 일반 Git 상태로 유지됩니다.

대화에서는 프롬프트와 에이전트 응답, 에이전트가 프로젝트를 탐색하고 파일을 편집하는 도구 활동, `/diff`로 검사할 수 있는 변경 사항의 세 가지 내용을 확인합니다.

## 대화를 시작하고 변경 요청하기

새 대화를 시작하여 기능 구현을 시작합니다.

1. Codespace로 돌아갑니다.
2. 이전에 터미널을 열어 두지 않았다면 <kbd>Control</kbd>+<kbd>\`</kbd>(Mac) 또는 <kbd>Ctrl</kbd>+<kbd>\`</kbd>(Windows/Linux)를 눌러 터미널을 엽니다.
3. Copilot이 열려 있지 않으면 다음 명령을 사용해 시작합니다.

   ```bash
   copilot --yolo
   ```

4. `/new` 슬래시 명령을 사용하고 <kbd>Enter</kbd>를 눌러 새 세션을 시작합니다.
5. 다음 프롬프트를 사용해 변경을 요청합니다.

   ```plaintext
   Show each game's starRating out of 5 in the game cards on the list page. If the rating is null, show "No rating yet". Keep the card layout as it is, add tests, and run the relevant checks.
   ```

Copilot은 프로젝트를 탐색하고 게임 상세 정보를 표시하는 파일을 찾은 뒤 필요한 코드를 생성합니다. 이제 Copilot CLI로 새 기능을 추가했습니다.

## diff 검토

작은 변경이라도 병합 전에 AI가 생성한 모든 변경 사항을 검토해야 합니다. Copilot CLI에서 변경 내용을 살펴봅니다.

1. `/diff`를 입력하고 변경된 모든 파일을 검사합니다.
2. 별점이 있으면 게임 카드에 숫자 별점을 표시하고 `starRating`이 `null`이면 `No rating yet`를 표시하는지 확인합니다.
3. 테스트가 두 상태 모두를 포함하는지 확인합니다.
4. Copilot이 실행한 검사 결과를 검토하고 실패가 있으면 수정하도록 요청합니다.
5. 검토를 마쳤으면 <kbd>Esc</kbd>를 눌러 diff 화면을 종료합니다.

> [!NOTE]
> 다른 생성형 AI 도구와 마찬가지로 Copilot은 결정론적이 아니라 확률적으로 작동하므로 정확한 코드가 달라질 수 있습니다. 정확히 같은 구현을 기대하기보다 동작을 검토합니다.

## 변경 사항 확인

코드를 읽는 것만으로는 충분하지 않습니다. Copilot에게 웹 사이트를 시작하도록 요청한 뒤 Codespaces가 전달한 브라우저에서 업데이트된 사용자 인터페이스(UI)를 확인합니다.

1. Copilot에 앱을 시작하도록 요청합니다.

   ```plaintext
   Start the app so I can inspect the star-rating change in my browser. Tell me the URL and leave the server running.
   ```

2. Codespaces에서 포트 `4321`을 사용할 수 있다고 표시되면 **Open in Browser**를 선택합니다.
3. 게임 카드에 별점이 5점 만점으로 표시되는지 확인합니다.
4. Copilot으로 돌아가 시작한 서버를 중지하도록 요청합니다.

   ```plaintext
   Stop the development server you started.
   ```

## 첫 풀 리퀘스트 열기 및 병합

이제 기능을 만들었습니다. 새 코드를 프로젝트에 병합할 풀 리퀘스트(PR)를 만들 차례입니다.

1. 기본 에이전트에게 변경 사항을 커밋하도록 요청합니다.

   ```plaintext
   Commit the reviewed star-rating changes with an appropriate commit message.
   ```

2. `/pr create`를 입력합니다. Copilot CLI는 PR을 만들 때 기존 커밋을 푸시하고 PR URL을 표시합니다.
3. <kbd>Command</kbd>(Mac) 또는 <kbd>Ctrl</kbd>(Windows/Linux)를 누른 채 Copilot CLI가 표시한 URL을 선택하여 PR을 엽니다.
4. 변경된 파일과 검사 결과를 검토합니다.
5. 준비가 되면 **Merge pull request**를 선택한 뒤 병합을 확인합니다.
6. Codespace로 돌아가 `/exit`로 Copilot CLI를 종료합니다.
7. 로컬 `main`을 업데이트합니다.

   ```bash
   git checkout main
   git pull
   ```

## 요약 및 다음 단계

축하합니다. GitHub Copilot CLI를 사용해 첫 변경 사항을 전달했습니다. 구체적으로 다음을 수행했습니다.

- 기능 브랜치에서 집중된 Copilot 대화를 시작했습니다.
- 에이전트에게 게임 카드의 작은 변경을 지시했습니다.
- `/diff`로 변경 사항을 검토했습니다.
- 전달된 브라우저에서 앱을 실행하여 별점 변경을 확인했습니다.
- 첫 풀 리퀘스트를 열고 병합했습니다.

다음으로 [필터링 이슈에서 시작하여 Plan 모드와 Autopilot 모드를 사용][next-lesson]해 더 큰 기능을 만듭니다.

## 리소스

- [GitHub Copilot CLI 정보][about-copilot-cli]
- [Copilot CLI 명령 참조][cli-reference]

[previous-lesson]: ../1-install-copilot-cli/
[next-lesson]: ../3-agent-modes/
[about-copilot-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
