---
title: "레슨 9 - GitHub Copilot CLI의 슬래시 명령"
description: "컨텍스트 관리, 모델 선택, 세션 공유, 선택적인 cloud agent 위임을 위한 슬래시 명령을 살펴봅니다."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

좋은 CLI 도구와 마찬가지로 GitHub Copilot CLI에는 상호 작용에 사용할 수 있는 다양한 슬래시 명령이 있습니다. 이러한 명령은 고급 기능, 내부 정보 및 추가 구성 옵션을 제공합니다. 이미 `/diff`, `/mcp`, `/skills`, `/agent`, `/pr` 같은 명령을 사용했습니다. 이제 몇 가지 유용한 명령을 더 살펴봅니다.

이 레슨에서는 다음을 수행합니다.

- `/context`와 `/compact`로 Copilot의 대화 컨텍스트 관리 방법을 살펴봅니다.
- `/model`로 사용 가능한 모델을 살펴봅니다.
- `/share`가 세션을 내보내거나 공유하는 방법을 배웁니다.
- 병렬 작업, worktree 및 cloud agent 위임을 위한 선택적 명령을 살펴봅니다.

## 시나리오

핵심 CLI 워크플로를 마쳤습니다. 이제 컨텍스트 관리, 모델 전환, 세션 공유, 선택적으로 [Copilot cloud agent][about-cloud-agent]에 작업 위임 같은 몇 가지 추가 기능을 살펴봅니다.

## Copilot CLI 컨텍스트 살펴보기

더 크거나 복잡한 작업을 수행할 때 모델의 최대 컨텍스트 창에 도달할 수 있습니다. Copilot CLI는 필요할 때 대화를 자동으로 압축하며 슬래시 명령으로 직접 검사하거나 압축할 수 있습니다.

1. Codespace로 돌아가 열려 있지 않으면 리포지토리 루트에서 Copilot CLI를 시작합니다.
2. 다음을 입력합니다.

   ```plaintext
   /context
   ```

3. 모델, 현재 토큰 사용량, 시스템 지침, 도구, 메시지 및 여유 공간으로 컨텍스트가 어떻게 나뉘는지 확인합니다.
4. 대화를 압축합니다.

   ```plaintext
   /compact
   ```

5. `/context`를 다시 입력하여 결과를 비교합니다. 대화가 이미 작으면 큰 변화가 없을 수 있습니다.

> [!NOTE]
> 컨텍스트 창이 차면 Copilot CLI가 자동으로 컨텍스트를 압축합니다. 압축 시점을 직접 선택하려면 `/compact`를 사용합니다. 관련 없는 작업으로 전환하고 새 대화를 시작하려면 `/clear` 또는 `/new`를 사용합니다.

## 모델 선택

모델마다 강점이 다르고 개발자마다 기본 설정이 다릅니다. Copilot CLI에서는 사용 가능한 모델을 나열하고 선택할 수 있습니다.

1. 다음을 입력합니다.

   ```plaintext
   /model
   ```

2. 사용 가능한 모델과 사용량 정보를 살펴봅니다.
3. 현재 모델을 유지하거나 다른 모델을 선택한 다음 <kbd>Esc</kbd>를 눌러 목록을 닫습니다.

## 세션 공유

팀이 함께 작업하고 배운 내용을 공유하면 모두가 AI 도구 사용법을 개선할 수 있습니다. `/share` 명령은 세션을 Markdown 또는 HTML 파일로 내보내고 공유 가능한 링크를 만들거나 GitHub gist로 게시할 수 있습니다.

1. `/help`를 입력하고 설치된 버전의 `/share` 옵션을 검토합니다.
2. 세션을 공유하려면 `/share file` 같은 로컬 Markdown 내보내기처럼 필요에 맞는 대상 유형을 선택합니다.
3. 다른 사람에게 보내거나 게시하기 전에 내보낸 내용을 검토합니다. 세션 내보내기에는 프롬프트, 응답 및 프로젝트 세부 정보가 포함될 수 있습니다.

링크 또는 gist 게시는 선택 사항입니다. 팀에서 공유할 의도가 없는 리포지토리 또는 대화 내용은 게시하지 않습니다.

## 선택 사항: 확장 또는 위임

핵심 워크숍을 완료했습니다. Copilot CLI는 더 큰 작업을 위한 명령도 제공합니다.

- `/fleet`은 독립적인 하위 작업을 하위 에이전트로 나누고 병렬로 실행할 수 있습니다.
- `/worktree`는 별도 작업을 위한 격리된 Git worktree를 만들 수 있습니다.
- `/delegate`은 작업을 비동기적으로 작동하며 풀 리퀘스트를 열 수 있는 Copilot cloud agent에 보낼 수 있습니다.

이러한 명령은 추가 worktree나 원격 작업을 만들 수 있으므로 선택 사항입니다. 사용하기 전에 새롭고 범위가 명확한 작업을 시작하고 정상적인 워크플로로 결과를 검토합니다. 비동기 에이전트 작업을 더 깊이 살펴보려면 [cloud agent 워크숍][cloud-workshop]을 계속합니다.

## 요약 및 다음 단계

Copilot CLI에서 슬래시 명령을 사용하면 구성하고 세션을 공유하며 내부 동작을 확인할 수 있습니다. 이 레슨에서는 다음을 수행했습니다.

- `/context`와 `/compact`로 Copilot의 대화 컨텍스트 관리 방법을 살펴봤습니다.
- `/model`로 사용 가능한 모델을 살펴봤습니다.
- `/share`가 세션을 내보내거나 공유하는 방법을 배웠습니다.
- 병렬 작업, worktree 및 cloud agent 위임을 위한 선택적 명령을 살펴봤습니다.

Copilot CLI에는 더 많은 슬래시 명령과 탐색할 기능이 있습니다. 이제 [배운 내용을 검토하고][next-lesson] 계속 학습하기 위한 다음 단계를 살펴보며 여정을 마무리합니다.

## 리소스

- [Copilot CLI 명령 참조][cli-reference]
- [Copilot CLI의 컨텍스트 관리][context-management]
- [Copilot cloud agent 정보][about-cloud-agent]

[previous-lesson]: ../8-create-pull-request/
[next-lesson]: ../10-review/
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[context-management]: https://docs.github.com/copilot/concepts/agents/copilot-cli/context-management
[about-cloud-agent]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[cloud-workshop]: ../../cloud/
