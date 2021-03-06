---
title: 如何：安装独立探查器 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 21a285c95e3649cc7aaa53995070091f0abea509
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-install-the-stand-alone-profiler"></a>如何：安装独立探查器
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 提供了一个基于命令行的独立探查器，它可在没有安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 的情况下运行。 当计算机没有安装或无法安装开发环境时会发生这种情况。 例如，不应在生产 Web 服务器上安装开发环境。  
  
> [!NOTE]
>  使用独立探查器收集 ASP.NET 网站的性能数据时，建议使用 [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) 命令行工具，而非 [VSPerfCmd](../profiling/vsperfcmd.md) 工具。  
  
### <a name="to-install-the-stand-alone-profiler"></a>安装独立探查器  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 安装媒体上包含 \Standalone Profiler 路径的目录中，找到独立探查器安装程序 (vs_profiler.exe)，然后运行该安装程序。  
  
2.  将 vsintr.exe 和 msdis150.dll 的路径添加到系统路径。  
  
    > [!NOTE]
    >  执行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的默认安装时，vsinstr.exe 和 msdis150.dll 位于 \Program Files\Visual Studio 10\Team Tools\Performance Tools 中。  
  
3.  在命令提示符处，键入 VSInstr。  
  
    > [!NOTE]
    >  如果显示 vsinstr.exe 的用法信息，则表明安装无误。 如果看见一条错误信息，该消息指出找不到 vsinstr.exe 或它的依赖项，请确保已经按步骤 2 中的说明正确设置了路径。  
  
4.  通过将 _NT_SYMBOL_PATH 变量设置为 symsrv\*symsrv.dll\*c:\localcache\*http://msdl.microsoft.com/download/symbols 来设置符号服务器  
  
5.  使用系统环境变量设置符号服务器后，请在新的命令提示符处运行命令行探查器工具。 这将使新环境变量生效。 在命令提示符窗口中，键入以下命令：  
  
     start %COMSPEC%  
  
    > [!NOTE]
    >  有关如何设置符号服务器包的详细说明，请参阅[如何：引用 Windows 符号信息](../profiling/how-to-reference-windows-symbol-information.md)。  
  
6.  使用 [VSPerfReport](../profiling/vsperfreport.md) 工具将符号串行化到分析数据 (.vsp) 文件中。 使用 VSPerfReport /summary:all /packsymbols 开关。 如果数据文件中未插入符号，请确保设置了 _NT_SYMBOL_PATH 环境变量。  
  
## <a name="see-also"></a>请参阅  
 [从命令行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [演练：使用采样进行命令行分析](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [演练：使用检测进行命令行分析](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [如何：引用 Windows 符号信息](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)