---
title: Python 环境窗口引用
description: 在 Visual Studio 的 Python 环境窗口中出现的每个选项卡的详细信息。
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 6ba46e41c8d6cd4feec4adc04f1470eed7744242
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="python-environments-window-tabs-reference"></a>“Python 环境”窗口选项卡引用

打开“Python 环境”窗口：

- 选择“查看”>“其他窗口”>“Python 环境”菜单命令。
- 在“解决方案资源管理器”中，右键单击某项目的“Python 环境”节点，选择“查看所有 Python 环境”

如果将“Python 环境”窗口展开到足够宽，这些选项将显示为选项卡，更便于使用。 为清楚起见，本文中的选项卡显示在扩展后的视图中。

![“Python 环境”窗口扩展后的视图](media/environments-expanded-view.png)

## <a name="overview-tab"></a>概述选项卡

为环境提供基本信息和命令：

![Python 环境概述选项卡](media/environments-overview-tab.png)

| 命令 | 描述 |
| --- | --- |
| 使此环境成为新项目的默认环境 | 设置活动环境，这可能会导致 Visual Studio（2017 版本 15.5 及更高版本）在加载 IntelliSense 数据库时短时间无响应。 含有多个包的环境可能无响应的时间更长。 |
| 访问分发服务器的网站 | 打开浏览器，访问 Python 分发所提供的 URL。 例如，对于 Python 3.x，会转到 python.org。 |
| 打开交互窗口 | 在 Visual Studio 中为此环境打开[交互 (REPL) 窗口](python-interactive-repl-in-visual-studio.md)，应用任何[启动脚本（见下文）](#startup-scripts)。 |
| 浏览交互式脚本 | 请参阅[启动脚本](#startup-scripts)。 |
| 使用 IPython 交互模式 | 设置后，将默认使用 IPython 打开交互窗口。 这样会启用内联绘图及扩展的 IPython 语法（如 `name?`）来查看 shell 命令的帮助和 `!command`。 建议在使用 Anaconda 分发时使用此选项，因为该选项需要额外的包。 有关详细信息，请参阅[在交互窗口中使用 IPython](interactive-repl-ipython.md)。 |
| 在 PowerShell 中打开 | 在 PowerShell 命令窗口中启动解释器。 |
| （文件夹和项目链接） | 提供对环境的安装文件夹、python.exe 解释器和 pythonw.exe 解释器的快速访问。 第一个会在 Windows 资源管理器中打开，后两个会打开控制台窗口。 |

### <a name="startup-scripts"></a>启动脚本

在日常工作流中使用交互窗口时，可能会开发定期使用的帮助器函数。 例如，可以创建用于在 Excel 中打开 DataFrame 的函数，然后将该代码保存为启动脚本，这样便始终可在交互窗口中使用该代码。

启动脚本包含交互窗口自动加载并运行的代码，包括导入、函数定义及任何其他文字内容。 此类脚本通过以下两种方式引用：

1. 安装环境时，Visual Studio 会创建文件夹 `Documents\Visual Studio 2017\Python Scripts\<environment>`，其中 &lt;environment&gt; 对应环境的名称。 可以使用“浏览交互式脚本”命令轻松地导航到特定于环境的文件夹。 启动该环境的交互窗口时，它会按字母顺序加载和运行在此处找到的任何 `.py` 文件。

1. “工具”>“选项”>“Python 工具”>“交互窗口”选项卡中的“脚本”控件（请参阅[交互窗口选项](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)）用于为所有环境中加载和运行的启动脚本指定另一个文件夹。 但是，此功能目前无效。

## <a name="configure-tab"></a>配置选项卡

如果可用，其中包含如下表中所述的详细信息。 如果此选项卡不显示，意味着 Visual Studio 自动管理所有详细信息。

![Python 环境配置选项卡](media/environments-configure-tab.png)

| 字段 | 描述 |
| --- | --- |
| **说明** | 为环境提供的名称。 |
| **前缀路径** | 解释程序的基本文件夹位置。 通过填写此值并单击“自动检测”，Visual Studio 会尝试填充其他字段。 |
| **解释器路径** | 解释器可执行文件的路径，通常是前缀路径后加 `python.exe` |
| **窗口化解释器** | 非控制台可执行文件的路径，通常是前缀路径后加 `pythonw.exe`。 |
| **库路径**<br/>（如果可用） | 指定标准库的根，但如果 Visual Studio 能够从解释器请求更准确的路径，可能会忽略此值。 |
| **语言版本** | 从下拉菜单中选择。 |
| **体系结构** | 通常自动检测并进行填充，否则指定 32 位或 64 位。 |
| **路径环境变量** | 解释器用来查找搜索路径的环境变量。 启动 Python 时 Visual Studio 更改该变量的值，使其包含项目的搜索路径。 此属性通常应设置为 `PYTHONPATH`，但某些解释器使用不同的值。 |

## <a name="packages-tab"></a>包选项卡

在先前版本中还标记为“pip”。

使用 pip 管理环境中安装的包，还允许搜索并安装新包（包括任何依赖项）。 Visual Studio 2017 15.7 版及更高版本中包含一个“包(Conda)”选项，该选项改为使用 conda 包管理器。 （如果未看到该选项，请设置选项“工具” > “选项” > “Python” > “实验性” > “可用时使用 conda 包管理器[而不是 pip]”，并重启 Visual Studio。）

将显示已安装的程序包，并带有更新（向上箭头）和卸载（圈圈中的 X）程序包的控件：

![Python 环境包选项卡](media/environments-pip-tab-controls.png)

输入搜索词筛选已安装的程序包的列表以及可从 PyPI 中安装的程序包。

![可以搜索“num”的 Python 环境程序包选项卡](media/environments-pip-tab.png)

还可以在搜索框中直接输入任何 `pip install` 命令，包括标志（例如 `--user` 或 `--no-deps`）。

安装一个包会在文件系统上环境的 `Lib` 文件中创建子文件夹。 例如，如果在 `c:\Python36` 中安装了 Python 3.6，则包会安装在 `c:\Python36\Lib` 中；如果在 `c:\Program Files\Anaconda3` 中安装了 Anaconda3，则包会安装在 `c:\Program Files\Anaconda3\Lib` 中。

在后一种情况下，由于环境位于文件系统的受保护区域 `c:\Program Files`，Visual Studio 必须以提升的权限运行 `pip install`，以使其能够创建包子文件夹。 需要提升时，Visual Studio 会显示提示，“可能需要管理员权限才能安装、更新或删除此环境的包”：

![针对包安装的提升提示](media/environments-pip-elevate.png)

“立刻提升”会将管理权限授予单个操作的 pip，同时取决于任何操作系统的权限提示。 选择“在没有管理员权限的情况下继续”会尝试安装该包，但尝试创建文件夹时 pip 会失败，同时会显示后列输出：“错误: 无法创建 'C:\Program Files\Anaconda3\Lib\site-packages\png.py': 权限被拒绝。”

选择“安装或删除包时始终提升”可防止针对相应环境出现该对话框。 若要再次显示对话框，请转到“工具”>“选项”>“Python 工具”>“常规”，选择按钮，重置所有永久隐藏的对话框。

在同一选项卡上，还可以选择“始终以管理员身份运行 pip”，针对所有环境禁止显示该对话框。 请参阅[选项 - “常规”选项卡](python-support-options-and-settings-in-visual-studio.md#general-options)。

## <a name="intellisense-tab"></a>IntelliSense 选项卡

显示 IntelliSense 完成数据库的当前状态：

![Python 环境 IntelliSense 选项卡](media/environments-intellisense-tab.png)

- 在 Visual Studio 2017 版本 15.5 和更早版本中，IntelliSense 完成依赖于为该库编译的数据库。 安装库后，将在后台生成数据库，但可能需要一些时间，并且可能在开始编写代码时此过程还未完成。
- Visual Studio 2017 15.6 版和更高版本默认使用更快的方法提供不依赖于数据库的完成。 因此，选项卡标记为“IntelliSense [数据库已禁用]”。 可通过清除选项“工具” > “选项” > “Python” > “实验性” > “针对环境使用新样式 IntelliSense”启用该数据库。

Visual Studio 检测到新环境（或添加一个）时，它会通过分析库源文件，自动开始编译数据库 。 此过程可能会花一分钟到一小时不等或者更多时间，具体取决于安装的组件。 （例如，Anaconda 随附了许多库，需要花费一些时间来编译该数据库。）完成后，会获得 IntelliSense 的详细信息，并且在安装更多库之前，无需再次刷新数据库（使用“刷新 DB”按钮）。

其中数据尚未编译的库将使用 **!** 标记；如果环境的数据库未完成，则 **!** 也会出现在主环境列表中该环境的旁边。

## <a name="see-also"></a>请参阅

- [在 Visual Studio 中管理 Python 环境](managing-python-environments-in-visual-studio.md)
- [为项目选择解释器](selecting-a-python-environment-for-a-project.md)
- [对依赖项使用 requirements.txt](managing-required-packages-with-requirements-txt.md)
- [搜索路径](search-paths.md)
