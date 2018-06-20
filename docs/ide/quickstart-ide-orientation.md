---
title: Visual Studio IDE 教程
ms.date: 11/15/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fd72de016e9f44987fae43e7b49820e21af0a288
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>快速入门：初步了解 Visual Studio IDE

在这个 5-10 分钟的 Visual Studio 集成开发环境 (IDE) 简介中，我们将介绍一些窗口、菜单和其他 UI 功能。

如果尚未安装 Visual Studio，请转到 [Visual Studio 下载](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)页免费安装。

## <a name="start-page"></a>起始页

启动 Visual Studio 之后你最先看到的很可能就是起始页。 起始页设计成一个“中心”，可帮助你更快地找到所需的命令和项目文件。 “最新动态”部分显示你最近处理的项目和文件夹。 在“新建项目”下，可以单击链接转到“新建项目”对话框中，或在“打开”下，可以打开现有项目或代码文件夹。 右侧是最新的开发人员新闻源。

![VS 起始页](media/quickstart-IDE-start-page.png)

如果关闭“起始页”并希望再次查看，则可以从“文件”菜单重新打开它。

![“文件”菜单](media/quickstart-IDE-file-menu-large.png)

若要继续浏览 IDE，我们需要先创建一个新项目。

1. 在“起始页”上，在“新建项目”下的搜索框中，输入 `console` 以筛选项目类型列表。 选择 C# 或 VB“控制台应用 (.NET Framework)”。 （或者，如果你是 C++、Javascript 或其他语言开发人员，请随意使用其中一种语言创建项目。 对于所有语言而言，查看时的 UI 都是相似的。）

1. 在“新建项目”对话框中，接受默认的项目名称并选择“确定”。

   创建项目，并在“编辑器”窗口中打开名为 Program.cs 或 Program.vb 的文件。 编辑器可显示文件的内容，是你在 Visual Studio 中完成大部分编码工作的地方。

## <a name="solution-explorer"></a>“解决方案资源管理器”

“解决方案资源管理器”可以显示项目、解决方案或代码文件夹中的文件和文件夹层次结构的图形表示。 你可以浏览层次结构，并导航到“解决方案资源管理器”中的某个文件。

![“解决方案资源管理器”](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>菜单

IDE 顶部的菜单栏将命令分组成不同的类别。 例如，“项目”菜单包含与你正在处理的项目相关的命令。 在“工具”菜单上，可通过选择“选项”自定义 IDE，或选择“获取工具和功能”向安装程序添加功能。

![菜单栏](media/quickstart-IDE-menu-bar.png)

可通过依次选择“视图”菜单和“错误列表”打开“错误列表”窗口。

## <a name="error-list"></a>错误列表

“错误列表”显示错误、警告以及有关当前代码状态的消息。 如果文件中或项目的任何地方出现错误（例如语法错误），则会在此处列出。

![错误列表](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>“输出”窗口

“输出”窗口为你显示版本生成和源代码管理的输出消息。

让我们构建该项目来查看一些输出记录。 从 **“生成”** 菜单中选择 **“生成解决方案”**。 “输出”窗口自动获得焦点并显示成功生成的消息。

![输出窗口](media/quickstart-IDE-output.png)

## <a name="quick-launch"></a>快速启动

“快速启动”框是在 IDE 中执行任何操作的快捷方式。 你可以输入一些与你想要执行的操作相关的文本，它会为你显示一个与文本相关的选项列表。 例如，假设我们要增加生成输出的详细程度，以显示有关确切生成内容的更多记录信息：

1. 将 `verbosity` 输入到“快速启动”框中，然后在“选项”类别下选择“项目和解决方案 -> 生成并运行”。

   ![“快速启动”框](media/quickstart-IDE-quick-launch.png)

   “选项”对话框打开，会显示“生成并运行”选项页。

1. 在“MSBuild 项目生成输出详细信息”下，选择“常规”，然后单击“确定”。

1. 现在，通过右键单击“解决方案资源管理器”中的“ConsoleApp1”项目，然后从上下文菜单中选择“重新生成”，我们可以重新生成项目。

   这次“输出”窗口显示了生成过程中更详细的日志记录，包括在哪里复制哪些文件。

## <a name="send-feedback-menu"></a>“发送反馈”菜单

如果你在使用 Visual Studio 时遇到任何问题，或者你有关于如何改进产品的建议，请使用 IDE 顶部“快速启动”框旁边的“发送反馈”菜单。

![“发送反馈”菜单](media/quickstart-IDE-send-feedback.png)

## <a name="next-steps"></a>后续步骤

我们只介绍了 Visual Studio IDE 的一些功能以便熟悉用户界面。 若要进一步了解，请继续：

- 浏览 VS 文档的“常规用户界面元素”部分，该部分对[错误列表](../ide/reference/error-list-window.md)、[输出](../ide/reference/output-window.md)、[属性](../ide/reference/properties-window.md)等窗口，以及[选项对话框](../ide/reference/options-dialog-box-visual-studio.md)进行了深入介绍

- 在 [Visual Studio IDE 概述](../ide/visual-studio-ide.md)中深入了解 IDE，甚至可初步了解代码调试

## <a name="see-also"></a>请参阅

- [快速入门：个性化设置 IDE](../ide/personalizing-the-visual-studio-ide.md)
- [快速入门：在编辑器中编码](../ide/quickstart-editor.md)
- [快速入门：项目和解决方案](../ide/quickstart-projects-solutions.md)
