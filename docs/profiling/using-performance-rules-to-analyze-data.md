---
title: 使用性能规则对数据进行分析 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ce42343167173647d39dcc6f7db06bedcbc0236
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2018
---
# <a name="using-performance-rules-to-analyze-data"></a>使用性能规则对数据进行分析
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的性能警告指示所分析应用程序中可能会减慢程序执行的问题。 警告还可指示可能需要更改收集方法才能收集更多有用的数据。 性能警告在分析会话中会自动生成。 在 Visual Studio 中打开分析数据文件时，这些警告将显示在“错误列表”窗口中。 从“错误列表”窗口中，可以找到问题的源代码，并且可以显示有关错误的详细信息（如有关如何解决问题的信息）。 还可以禁用不感兴趣的警告。  
  
> [!NOTE]
>  探查器性能警告由程序执行的动态分析生成，独立于代码分析警告。 代码分析还会基于源代码的静态分析为托管代码生成性能警告。 有关详细信息，请参阅[分析托管代码质量](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)和[性能警告](../code-quality/performance-warnings.md)。  
  
## <a name="in-this-section"></a>本节内容  
 [如何：查看性能警告](../profiling/how-to-view-performance-warnings.md)  
 提供有关如何打开“错误列表”窗口以查看探查器性能警告的信息。  
  
 [如何：配置性能规则](../profiling/how-to-configure-performance-rules.md)  
 提供有关如何启用或禁用各个性能警告的信息。  
  
 [性能规则参考](../profiling/performance-rules-reference.md)  
 提供有关探查器性能警告的详细信息