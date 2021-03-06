---
title: 工作流设计器-Pick 活动设计器
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f664ac3a22b91780d392e0fef3224cd80b1e7919
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="pick-activity-designer"></a>Pick 活动设计器

<xref:System.Activities.Statements.Pick> 活动提供基于事件的控制流。 该活动执行多个分支中的一个分支来响应某个触发的事件。

## <a name="the-pick-activity"></a>Pick 活动

<xref:System.Activities.Statements.Pick> 活动包含一个 <xref:System.Activities.Statements.PickBranch> 对象的集合，<xref:System.Activities.Statements.Pick> 活动会由于某些作为触发器的传入事件而执行其中一个对象。 在这种方式 Windows 工作流设计器提供基于事件的控制流建模。 每个 <xref:System.Activities.Statements.PickBranch> 都包含一个 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 和一个 <xref:System.Activities.Statements.PickBranch.Action%2A>。 开头的<xref:System.Activities.Statements.Pick>活动的执行的所有触发器活动<xref:System.Activities.Statements.PickBranch>计划元素。 在第一个活动完成之后，安排其相应的操作活动，并且取消所有其他触发器活动。

### <a name="how-to-use-the-pick-activity-designer"></a>如何使用 Pick 活动设计器

**选取**在找不到活动设计器**控制流**类别**工具箱**，通过单击访问的哪一**工具箱**工作流设计器上的选项卡 (或者，选择**工具栏**从**视图**菜单或 CTRL + ALT + X。)

**选取**活动设计器可以拖动从**工具箱**和放置到工作流设计器图面，只要通常放置活动设计器，例如内**序列**活动设计器。 将它放到工作流设计器中，完成后，它创建<xref:System.Activities.Statements.Pick>活动，其中默认情况下包含两个空<xref:System.Activities.Statements.PickBranch>活动，作为元素的显示名称为 Branch1 和 Branch2。 二者各自<xref:System.Activities.Statements.PickBranch.DisplayName%2A>属性值可以在中编辑**pickbranch**活动设计器标头或**属性**为每个分支的窗口。

有两种方法来添加<xref:System.Activities.Statements.PickBranch>到的集合的活动<xref:System.Activities.Statements.Pick>对象： 中拖放**pickbranch**从设计器**工具箱**或通过从上下文菜单在**选取**设计图面。 有关详细信息，请参阅[pickbranch](../workflow-designer/pickbranch-activity-designer.md)主题。 请注意，唯一项可以放置在**选取**活动设计器是**pickbranch**活动设计器。

### <a name="pick-activity-properties-in-the-workflow-designer"></a>工作流设计器中的 Pick 活动属性

下表列出 <xref:System.Activities.Statements.Pick> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中或设计器图面上进行编辑。

|属性名|必需|用法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Pick> 活动设计器在标头中的友好名称。 默认值为 Pick。 可以在属性网格或直接在活动设计器的标头中编辑该值。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|

## <a name="see-also"></a>请参阅

- [控制流](../workflow-designer/control-flow-activity-designers.md)
- [Pick 活动](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [使用 Pick 活动](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)