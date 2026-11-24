---
title: "练习 0：先决条件"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

在开始 Copilot 云代理练习之前，需要先完成环境准备。你将创建 Tailspin Toys 存储库的副本，并启动可用于编辑指令文件及审阅云代理工作结果的 [codespace][codespaces]。

## 设置实验室存储库

若要创建用于编写代码的存储库副本，请从 [模板][template-repository] 创建实例。新实例包含实验室所需的全部文件，后续练习将使用该实例。

1. 在新浏览器窗口中打开 [Tailspin Toys 模板][tailspin-template]。
2. 在实验室存储库页面选择 **Use this template** 按钮，然后选择 **Create a new repository**。

    ![Use this template 按钮](../../../_images/ex0-use-template.png)

3. 如果通过 GitHub 或 Microsoft 举办的活动参加本工作坊，请按讲师提供的说明操作；否则，可在可以访问 GitHub Copilot 的组织中创建新存储库。

    ![存储库模板设置](../../../_images/ex0-repository-settings.png)

4. 记下创建的存储库路径（**organization-or-user-name/repository-name**），后续练习会用到。

## 创建 codespace

接下来使用 codespace 完成实验室练习。[GitHub Codespaces][codespaces] 是云端开发环境，可直接在浏览器中编写、运行和调试代码，并提供支持多种编程语言、扩展和工具的完整 IDE。

1. 打开新建的存储库。
2. 选择绿色的 **Code** 按钮。
3. 选择 **Codespaces** 选项卡，然后选择 **+** 创建新的 Codespace。

    ![创建新的 codespace](../../../_images/ex0-create-codespace.png)

创建 codespace 通常需要几分钟；可借此了解 GitHub Copilot 的其他功能。

> [!CAUTION]
> 后续练习会再次使用此 codespace。当前请将它保留在浏览器标签页中。

> [!NOTE]
> 本工作坊可在 codespace 或本地 [开发容器][dev-containers] 中运行。两者都会预装必要的前置依赖。若选择本地运行，请打开克隆后的存储库，在 VS Code 中提示时选择 **Reopen in Container**。

[codespaces]: https://github.com/features/codespaces
[dev-containers]: https://code.visualstudio.com/docs/devcontainers/containers

## 总结

恭喜，你已创建实验室存储库副本，并开始创建 codespace；后续会在其中与 Copilot 云代理协作。

## 下一步

让我们添加云代理遵循的自定义指令。继续阅读 [练习 1：自定义指令][next-lesson]。

## 资源

- [GitHub Codespaces 概览][codespaces]
- [从模板创建存储库][template-repository]
- [Codespaces 入门][codespaces-quickstart]

[tailspin-template]: https://github.com/github-samples/tailspin-toys
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[codespaces-quickstart]: https://docs.github.com/codespaces/getting-started/quickstart
[next-lesson]: ../1-custom-instructions/
