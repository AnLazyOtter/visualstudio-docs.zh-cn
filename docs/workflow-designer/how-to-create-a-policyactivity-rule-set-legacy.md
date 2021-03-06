---
title: 工作流设计器-如何： 创建 PolicyActivity 规则集 （旧版）
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57142fc21bc9db03a338f20a27e20b8af51b48cd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>如何：创建 PolicyActivity 规则集（旧版）

本主题介绍如何创建策略活动规则集使用旧的 Windows 工作流设计器面向.NET Framework 版本 3.5 或 WinFX。

 在拖动之后**策略**活动项从**工具箱**到工作流设计图面上，你将想要选择现有的规则或创建新规则集[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)活动。 选择现有的规则使用设置[选择规则设置对话框 （旧版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)并通过使用创建规则集[规则设置编辑器对话框 （旧版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)。

> [!NOTE]
> 你可以打开[规则设置编辑器对话框 （旧版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)直接通过双击对话框[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)是工作流设计图面的活动。

## <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>为 PolicyActivity 活动选择或创建规则集

1.  右键单击[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)，然后单击**属性**以打开**属性**窗口。

2.  单击**rulesetreference**属性。

3.  执行下列操作之一：

    -   单击**rulesetreference**省略号 **[…]**，然后选择现有规则中设置[选择规则设置对话框 （旧版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)。 然后转到步骤 10。

         - 或 -

    -   键入规则集的名称。 单击**rulesetreference**省略号 **[…]**，然后选择**编辑**中[选择规则设置对话框 （旧版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)。

         -或-

    -   键入规则集的名称。 展开**rulesetreference**属性并选择省略号 **[…]** 中**RuleSet 定义**属性。

         [规则设置编辑器对话框 （旧版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)打开。

4.  在[规则设置编辑器对话框 （旧版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)，单击**添加规则**以向规则集添加新规则。

5.  输入**名称**，**优先级**，和**重新评估**属性，或保留默认值。

6.  输入的文本**条件**。

7.  输入的文本**Then 操作**和**Else 操作**。

8.  单击**添加规则**以添加另一个规则。

9. 完成后单击“确定” 。

## <a name="see-also"></a>请参阅

- [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)
- [“选择规则集”对话框（旧版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)
- [“规则集编辑器”对话框（旧版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)
- [使用策略活动](http://go.microsoft.com/fwlink?LinkID=65004)
- [旧版工作流活动](../workflow-designer/legacy-workflow-activities.md)