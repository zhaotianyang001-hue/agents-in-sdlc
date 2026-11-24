---
title: "레슨 6 - Playwright MCP로 기능 검증"
description: "Copilot CLI에서 Playwright MCP를 검사하거나 구성하고 브라우저에서 필터링 기능을 살펴봅니다."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

앞서 강조했듯이 코드를 작성하는 것보다 더 많은 작업이 필요합니다. 데이터와 외부 서비스를 다루고 Copilot에서 사용할 수 있는 추가 자동화를 제공해야 합니다. 이때 MCP 서버가 사용됩니다. MCP 서버는 Copilot이 CLI에 기본 제공되는 기능을 넘어서 더 많은 도구와 서비스를 사용할 수 있게 합니다.

이 레슨에서는 다음을 수행합니다.

- Model Context Protocol(MCP)이 무엇이고 Copilot CLI에서 어떻게 사용하는지 이해합니다.
- Playwright MCP 서버를 사용할 수 없으면 추가합니다.
- 에이전트에게 브라우저를 조작하여 필터링 기능을 살펴보도록 요청합니다.

## 시나리오

단위 테스트와 엔드투엔드 테스트도 중요하지만 UI 업데이트를 검증하려면 실제로 UI와 상호 작용해야 합니다. 사용자가 작업 중인 웹 사이트를 사용할 수 있도록 Copilot을 설정하여 변경의 자동 검증을 강화하고 업데이트가 예상대로 작동하는지 더 확신할 수 있습니다.

## Model Context Protocol(MCP)이란?

[Model Context Protocol(MCP)][mcp-blog-post]는 AI 에이전트가 외부 도구 및 서비스와 통신하는 방법을 제공합니다. MCP를 사용하면 AI 에이전트가 실시간으로 외부 도구 및 서비스와 통신할 수 있습니다. 따라서 최신 정보에 접근하고 사용자를 대신해 작업을 수행할 수 있습니다.

이러한 도구와 리소스는 AI 에이전트와 외부 도구 및 서비스 사이의 다리 역할을 하는 MCP 서버를 통해 액세스됩니다. 각 MCP 서버는 AI 에이전트가 사용할 수 있는 서로 다른 도구와 리소스 세트를 나타냅니다.

널리 사용되는 MCP 서버는 다음과 같습니다.

- **[GitHub MCP 서버][github-mcp]**: GitHub 리포지토리, 이슈, 풀 리퀘스트를 관리하는 API에 액세스할 수 있습니다.
- **[Playwright MCP 서버][playwright-mcp-server]**: Playwright를 사용한 브라우저 자동화 기능을 제공합니다.

그 외에도 다양한 MCP 서버를 사용할 수 있습니다. GitHub는 생태계의 검색과 기여를 강화하기 위해 [MCP 레지스트리][mcp-registry]를 제공합니다.

> [!CAUTION]
> MCP 서버는 프로젝트의 다른 종속성과 동일하게 취급합니다. 사용하기 전에 소스 코드를 검토하고 게시자를 확인하며 보안 영향을 고려합니다.

## Playwright MCP 서버 추가

Playwright MCP 서버를 사용할 수 없는 경우 서버를 추가하여 Copilot이 사용자가 사용하는 방식으로 웹 사이트와 상호 작용하도록 합니다.

> [!NOTE]
> Playwright MCP가 이미 Copilot CLI에 구성되어 있으면 다음 섹션으로 건너뜁니다.

1. Codespace로 돌아갑니다.
2. Copilot CLI에서 다음 명령을 입력하여 MCP 서버 추가 대화 상자를 엽니다.

   ```plaintext
   /mcp add
   ```

3. 이름에 `playwright`를 입력한 다음 <kbd>Tab</kbd>을 누릅니다.
4. <kbd>Enter</kbd>를 눌러 서버 유형이 **STDIO**인지 확인한 다음 <kbd>Tab</kbd>을 누릅니다.
5. 다음 명령을 **Command** 대화 상자에 붙여넣습니다.

   ```plaintext
   npx -y @playwright/mcp@latest --headless --no-sandbox
   ```

6. <kbd>Control</kbd>+<kbd>S</kbd>(Mac) 또는 <kbd>Ctrl</kbd>+<kbd>S</kbd>(Windows/Linux)를 눌러 새 MCP 서버를 저장합니다.
7. <kbd>Esc</kbd>를 눌러 MCP 대화 상자를 종료합니다.

## Playwright를 통해 Copilot에 기능 탐색 요청

이전에 수동으로 기능이 예상대로 작동하는지 확인했습니다. 이제 Copilot에서 제공하는 Playwright MCP 서버를 사용해 같은 검사를 수행합니다.

1. 다음 프롬프트를 사용하여 Copilot이 Playwright MCP 서버로 기능을 검증하도록 요청합니다.

   ```plaintext
   Start the app and use Playwright MCP to check filtering against the issue and our plan. Tell me what works and what doesn't, without making changes. Stop the server you started when you're done.
   ```

> [!NOTE]
> Copilot은 일반적으로 MCP 서버를 알아서 사용하므로 실제로 사용하도록 명시할 필요는 없습니다. 그러나 사용할 서버를 알고 있다면 올바른 방향을 안내하는 것이 나쁠 것은 없습니다. 이 방법은 일관된 결과를 얻고 토큰도 절약하는 데 도움이 됩니다.

2. Copilot이 브라우저에서 기능이 작동하는지 확인하기 위해 수행하는 여러 단계를 살펴봅니다.
3. 보고서를 읽고 모든 동작이 예상대로인지 확인합니다.

Copilot은 서버를 시작하고 Playwright로 웹 사이트와 상호 작용한 다음 서버를 중지하고 보고서를 제공합니다.

## 요약 및 다음 단계

축하합니다. Copilot CLI에서 Playwright MCP 서버를 사용하여 실제 브라우저로 기능을 살펴봤습니다. 요약하면 다음을 수행했습니다.

- Model Context Protocol(MCP)이 무엇이고 Copilot CLI에서 사용하는 방법을 배웠습니다.
- Playwright MCP 서버를 사용할 수 없으면 추가했습니다.
- 에이전트에게 브라우저를 조작하여 필터링 기능을 살펴보도록 요청했습니다.

다음으로 스킬과 브라우저 도구를 전문 역할로 결합하는 [QA 사용자 지정 에이전트를 만듭니다][next-lesson].

## 리소스

- [MCP가 무엇이고 왜 모두가 이야기할까요?][mcp-blog-post]
- [Microsoft Playwright MCP 서버][playwright-mcp-server]
- [Copilot CLI에 MCP 서버 추가][add-mcp]

[previous-lesson]: ../5-agent-skills/
[next-lesson]: ../7-qa-agent/
[mcp-blog-post]: https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/
[playwright-mcp-server]: https://github.com/microsoft/playwright-mcp
[github-mcp]: https://github.com/github/github-mcp-server
[mcp-registry]: https://github.com/mcp
[add-mcp]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-mcp-servers
