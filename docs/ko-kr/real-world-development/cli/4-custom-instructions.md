---
title: "레슨 4 - 사용자 지정 지침으로 Copilot 안내"
description: "리포지토리 지침을 살펴보고 문서화 표준을 추가한 뒤 필터링 코드에 적용합니다."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

생성형 AI를 사용할 때는 컨텍스트가 핵심입니다. 특정 방식으로 작업을 수행해야 한다면 Copilot이 해당 지침을 사용할 수 있어야 합니다. [지침 파일][instruction-files]은 원하는 코드뿐 아니라 코드의 구조화 방법도 설명합니다. 필터링을 구현했으므로 Copilot이 사용한 지침을 살펴보고 문서화 표준을 추가한 뒤 코드에 적용합니다.

이 레슨에서는 다음을 수행합니다.

- 리포지토리 지침과 경로 범위 지침 파일이 에이전트에 전달되는 방식을 살펴봅니다.
- 지침 파일을 업데이트하여 코딩 표준을 따르도록 합니다.
- 지침 파일이 코드에 미치는 영향을 확인합니다.

## 시나리오

훌륭한 개발 팀인 Tailspin Toys에는 개발 관행에 대한 지침과 요구 사항이 있습니다. 여기에는 다음 내용이 포함됩니다.

- 주석은 코드를 반복하지 않고 의도를 설명하고 명확하지 않은 결정 사항을 설명해야 합니다.
- `db/`와 `src/lib/`의 내보낸 함수는 목적, 매개 변수, 반환 값을 TSDoc/JSDoc으로 문서화하고, 해당되는 경우 주입 가능한 `db` 인수를 포함해야 합니다.
- 재사용 가능한 Astro 컴포넌트는 `Props` 계약을 문서화하고 관련 코드가 변경되면 주석도 최신 상태로 유지해야 합니다.
- 기존 서식과 린트 지침은 유지해야 합니다.

지침 파일을 사용하면 Copilot이 강조된 관행에 맞게 작업을 수행하는 데 필요한 정보를 제공합니다.

## 지침 파일

사용자 지정 지침을 사용하면 Copilot에 컨텍스트와 기본 설정을 제공하여 코딩 스타일과 요구 사항을 더 잘 이해하도록 할 수 있습니다. 이 강력한 기능은 더 적합한 제안과 코드 스니펫을 얻도록 Copilot을 안내합니다. 선호하는 코딩 규칙, 라이브러리, 포함할 주석 유형을 지정할 수 있습니다. 전체 리포지토리 또는 특정 파일 유형에 대한 지침을 만들어 작업 수준 컨텍스트를 제공할 수 있습니다.

지침 파일에는 두 가지 유형이 있습니다.

- `.github/copilot-instructions.md`: 리포지토리의 **모든** 요청에 Copilot에 전달되는 단일 지침 파일입니다. 이 파일에는 대부분의 요청과 관련된 프로젝트 수준 정보가 포함되어야 합니다.
- `.github/instructions/*.instructions.md`: 특정 언어나 파일 유형 또는 작업에 대한 지침을 제공합니다.

> [!NOTE]
> 지침 형식과 지원 범위는 환경마다 다릅니다. 특정 형식에 의존하기 전에 [사용자 지정 지침 지원 참조][custom-instructions-support]를 확인합니다.

## 이 프로젝트의 사용자 지정 지침 파일 살펴보기

시작을 돕기 위해 스타터 프로젝트에 이미 지침 파일을 포함했습니다. 변경 사항이 미치는 영향을 확인하기 전에 기존 내용을 살펴봅니다.

1. Codespace로 돌아갑니다.
2. Codespaces 편집기(터미널이 아닌 곳)에서 `.github/copilot-instructions.md`를 엽니다.
3. 프로젝트의 간략한 설명과 코딩 지침을 확인합니다. 이 지침은 이 리포지토리에서 Copilot과 상호 작용할 때 모두 적용됩니다.
4. `.github/instructions` 폴더를 열고 파일을 살펴봅니다. Astro 파일, Drizzle 데이터 계층, 테스트 등에 대한 지침이 있습니다.
5. `.github/instructions/unit-tests.instructions.md`를 엽니다. 맨 위의 `applyTo` 필드에 지침이 적용되는 파일을 결정하는 glob이 설정되어 있습니다.
6. `.github/instructions/drizzle.instructions.md`를 열고 다른 지침 파일과 기존 프로젝트 파일로 연결되는 링크를 확인합니다. 이렇게 하면 큰 지침 세트를 작고 재사용 가능한 파일로 나누고 따라야 할 예제를 Copilot에 제공할 수 있습니다.

## 팀 지침에 맞게 지침 파일 업데이트하기

기존 파일은 좋은 출발점이지만 격차가 있습니다. 새로 생성하는 TypeScript에 TSDoc 주석을 추가하도록 핵심 `copilot-instructions.md` 파일을 수정합니다.

1. `.github/copilot-instructions.md`에서 약 35번째 줄 주변의 **Code formatting guidance** 섹션을 찾습니다.
2. 다음 내용을 마지막 글머리 기호로 추가합니다.

   ```markdown
   - All new TypeScript should contain TSDocs comments for documentation purposes.
   ```

파일은 자동으로 저장됩니다.

## 업데이트된 지침 사용하기

Copilot CLI는 대화를 시작할 때 리포지토리 지침을 로드합니다. 업데이트된 지침을 저장한 후 필터링 대화를 종료하고 다시 시작하여 기능 컨텍스트를 잃지 않고 새 지침으로 시작하게 합니다.

1. 필터링 대화가 열려 있으면 `/exit`를 입력하여 닫습니다. Copilot CLI는 대화를 자동으로 저장합니다.
2. `game-filters-cli` 브랜치의 리포지토리 루트에서 저장된 대화를 다시 시작합니다.

   ```bash
   copilot --resume
   ```

   메시지가 표시되면 필터링 대화를 선택하고 `game-filters-cli` 브랜치가 체크아웃되어 있는지 확인합니다.
3. Copilot에게 업데이트된 지침을 적용하도록 요청합니다.

   ```plaintext
   We just updated our instructions and code guidance. Can you please update the code you generated to match that guidance?
   ```

4. `/diff`를 입력하고 변경된 TypeScript 파일을 읽습니다. 새로 생성된 TSDoc 주석이 코드를 정확하게 설명하는지 확인합니다.

## 요약 및 다음 단계

Copilot CLI가 지침 파일에서 컨텍스트를 가져오는 방법을 살펴보고 기능에 새 표준을 적용했습니다. 구체적으로 다음을 수행했습니다.

- 리포지토리 지침과 경로 범위 지침 파일이 에이전트에 전달되는 방식을 살펴봤습니다.
- 지침 파일을 업데이트하여 코딩 표준을 따르도록 했습니다.
- 지침 파일이 코드에 미치는 영향을 확인했습니다.

다음으로 [재사용 가능한 quality-checks 스킬을 사용자 지정하고 실행][next-lesson]하여 린트와 테스트가 일관되게 실행되도록 합니다.

## 리소스

- [Copilot CLI용 사용자 지정 지침 추가][instruction-files]
- [사용자 지정 지침 지원][custom-instructions-support]
- [사용자 지정 지침 작성 모범 사례][instructions-best-practices]
- [Awesome Copilot — 지침 파일 및 기타 리소스 모음][awesome-copilot]

[instruction-files]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-custom-instructions
[instructions-best-practices]: https://docs.github.com/copilot/concepts/prompting/response-customization#writing-effective-custom-instructions
[awesome-copilot]: https://awesome-copilot.github.com/
[custom-instructions-support]: https://docs.github.com/copilot/reference/custom-instructions-support
[previous-lesson]: ../3-agent-modes/
[next-lesson]: ../5-agent-skills/
