---
title: 工作流设计器-如何： 使用工作流设计器调试 XAML
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: eac6294861080614cbdd46e6ac1cc9a05d7124ff
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>如何：使用工作流设计器调试 XAML

工作流是以 XAML 的形式定义的。 工作流的 UI 表示形式建立在定义该工作流的 XAML 树之上。 调试体验是类似于调试 Windows 工作流设计器中的工作流。 例如，调试 XAML 时，局部变量、 监视，以及线程窗口适用相同的方式与它们在工作流设计器调试。 此外，在 XAML 调试过程中，“调用堆栈”视图是工作流执行流的基于行的分层视图。

> [!NOTE]
> 如果工作流的 XAML 位于活动所在的同一程序集中，将不包括类名称的程序集部分。 没有类（活动）名称的此部分，将不能在运行时加载 XAML。 建议不要在主项目所在的同一命名空间中定义活动；否则，在设计器中编辑后需要手动编辑 XAML。

## <a name="to-debug-workflow-xaml"></a>调试工作流 XAML

1.  在 Visual Studio 中打开工作流或活动项目。

2.  在活动或你想要调试中所述的活动上设置断点[如何： 在工作流中设置断点](../workflow-designer/how-to-set-breakpoints-in-workflows.md)。

3.  右键单击包含您的工作流定义和选择.xaml 文件**查看代码**。 您将看到在设计视图中对其设置了断点的活动的 XAML 元素声明所在行中显示了一个断点。

4.  中所述调用调试器[如何： 调用工作流调试器](../workflow-designer/how-to-invoke-the-workflow-debugger.md)。

5.  当代码执行到你设置的其中一个断点处时，与该断点关联的 XAML 元素将突出显示。 若要将移到下一个断点，使用**F10**或**F11**密钥。

## <a name="see-also"></a>请参阅

- [如何：在工作流中设置断点](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [如何：调用工作流调试器](../workflow-designer/how-to-invoke-the-workflow-debugger.md)