---
title: VCMessage 任务 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa8ef67a4fa19bd715e73e50fcc268aee7a4df5d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2018
---
# <a name="vcmessage-task"></a>VCMessage 任务
记录生成期间的警告消息和错误消息。  
  
## <a name="remarks"></a>备注  
 此任务可帮助实现 Visual C++ 的 MSBuild，不能由用户调用。 有关更多信息，请参见<xref:Microsoft.Build.Utilities.TaskLoggingHelper>。  
  
## <a name="parameters"></a>参数  
 下表描述了 VCMessage 任务的参数。  
  
|参数|描述|  
|---------------|-----------------|  
|**参数**|可选 **String** 参数。<br /><br /> 要显示的消息列表（以分号分隔）。|  
|**代码**|必需的 **String** 参数。<br /><br /> 限定消息的错误号。|  
|**Type**|可选 **String** 参数。<br /><br /> 指定要发出的消息类型。 指定 `"Warning"` 发出一条警告消息，或指定 `"Error"` 发出一条错误消息。|  
  
## <a name="see-also"></a>请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)