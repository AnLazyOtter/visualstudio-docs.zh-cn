---
title: "如何：以编程方式在创建范围时排除段落标记"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "文档 [Visual Studio 中的 Office 开发]，排除段落"
  - "范围，排除 Word 中的段落标记"
  - "文档 [Visual Studio 中的 Office 开发]，段落标记"
  - "段落，控制结构"
ms.assetid: 6d563834-34bd-4462-a556-4339d9277eee
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# 如何：以编程方式在创建范围时排除段落标记
  当你创建基于段落的 <xref:Microsoft.Office.Interop.Word.Range> 对象时，所有非打印字符（如段落标记）都将纳入范围。 可将源段落的文本插入到目标段落。 如果不希望将目标段落拆分为单独的段落，则必须先从源段落中删除段落标记。 此外，由于段落标记中存储着段落格式设置信息，所以当你将范围插入到现有段落时可能需要删除它。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 以下示例过程声明两个字符串变量，检索活动文档中的第一个和第二个段落的内容，然后交换它们的内容。 随后，该示例将演示如何通过使用 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 方法并在段落中插入文本，从范围中删除段落标记。  
  
### 在插入文本时控制段落结构  
  
1.  为第一个和第二个段落创建两个范围变量，并使用 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 属性检索其内容。  
  
     下面的代码示例可用于文档级自定义项。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomation#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#27)]  
  
     以下代码示例可用于应用程序级 VSTO 外接程序。 此代码运用了活动文档。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
2.  分配 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 属性，在两个段落间交换文本。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#28)]
     [!code-vb[Trin_VstcoreWordAutomation#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#28)]  
  
3.  依次选择每个范围并暂停，在消息框中显示结果。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#29)]
     [!code-vb[Trin_VstcoreWordAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#29)]  
  
4.  使用 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 方法调整 `firstRange`，使 `firstRange` 中不再含有段落标记。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreWordAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#30)]  
  
5.  替换第一个段落中的剩余文本，向该范围的 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 属性分配一个新字符串。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreWordAutomation#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#31)]  
  
6.  替换 `secondRange` 中的文本，包括段落标记。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#32)]
     [!code-vb[Trin_VstcoreWordAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#32)]  
  
7.  选择 `firstRange` 并暂停以便在消息框中显示结果，然后对 `secondRange` 执行相同操作。  
  
     由于已将 `firstRange` 重定义为排除段落标记，所以保留了该段落的原始格式。 但是，在 `secondRange` 中的段落标记上插入了句子，从而删除了单独的段落。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#33)]
     [!code-vb[Trin_VstcoreWordAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#33)]  
  
     两个区域的原始内容均保存为字符串，因此你可以将文档还原到其原始状态。  
  
8.  对一个字符位置使用 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 方法，将 `firstRange` 重新调整为包含段落标记。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#34](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreWordAutomation#34](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#34)]  
  
9. 删除 `secondRange`。 此操作将第三个段落还原到其原始位置。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#35](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#35)]
     [!code-vb[Trin_VstcoreWordAutomation#35](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#35)]  
  
10. 还原 `firstRange` 中的原始段落文本。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#36](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#36)]
     [!code-vb[Trin_VstcoreWordAutomation#36](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#36)]  
  
11. 使用 <xref:Microsoft.Office.Interop.Word.Range> 对象的 <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> 方法，将第二个段落的原始内容插入到 `firstRange` 之后，并选择 `firstRange`。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#37](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#37)]
     [!code-vb[Trin_VstcoreWordAutomation#37](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#37)]  
  
## 文档级自定义项示例  
  
#### 在文档级自定义项中插入文本时控制段落结构  
  
1.  下面的示例显示针对文档级自定项的完整方法。 若要使用此代码，请从项目中的 `ThisDocument` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#26)]  
  
## VSTO 外接程序示例  
  
#### 在 VSTO 外接程序中插入文本时控制段落结构  
  
1.  下面的示例显示针对 VSTO 外接程序的完整方法。 若要使用此代码，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
## 请参阅  
 [如何：以编程方式在文档中扩展范围](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何：以编程方式折叠文档中的范围或选定内容](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [如何：以编程方式在 Word 文档中插入文本](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [如何：以编程方式重置 Word 文档中的范围](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [如何：以编程方式在文档中定义和选择范围](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  