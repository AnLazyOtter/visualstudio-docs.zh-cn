---
title: CvInitProvider 函数 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c8e3b082c57e48d7c70fdda22c68c1a9d8980f71
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2018
---
# <a name="cvinitprovider-function"></a>CvInitProvider 函数
初始化标记提供程序。 必须在任何其他并发可视化工具 SDK 函数之前调用。  
  
## <a name="syntax"></a>语法  
  
```C  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pGuid`  
 提供程序 GUID。 不能为 NULL。  
  
 `ppProvider`  
 输出变量的地址，用于存储提供程序上下文。 不能为 NULL。  
  
## <a name="return-value"></a>返回值  
 成功初始化提供程序时返回 S_OK，出现任何错误时返回错误代码。 使用 SUCCEEDED/FAILED 宏检查错误条件。  
  
## <a name="requirements"></a>惠?  
 **标头：** cvmarkers.h  
  
## <a name="see-also"></a>请参阅  
 [C++ 库参考](../profiling/cpp-library-reference.md)