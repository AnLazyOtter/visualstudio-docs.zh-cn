---
title: GPU 活动(其他进程) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 586aeb9b2b6d674c14106a911872c967c272f3e6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2018
---
# <a name="gpu-activity-other-processes"></a>GPU 活动(其他进程)
并发可视化工具的“线程”视图中的“GPU 活动(其他进程)”段表示 GPU 代表系统上的其他进程处理请求的时间。 这些请求以直接内存访问 (DMA) 数据包的形式发送到 GPU。  段的长度代表 GPU 处理数据包的持续时间。  
  
 当选择此类型段时，“当前”选项卡上的报告将显示所处理的数据包的相关信息。  此信息包括数据包在与 DirectX 引擎关联的硬件队列中等待的总时间、提交数据包的进程，以及处理数据包所需的时间。