---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider 函数 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6198cfc874eb8a547b77bfabe8b3fb3473fa92ef
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2018
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider 函数
创建默认提供程序的默认标记系列。  
  
## <a name="syntax"></a>语法  
  
```C  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppProvider`  
 提供程序对象变量的地址。 地址不能为 NULL，该变量可以具有任何值。  
  
 `ppMarkerSeries`  
 标记系列对象变量的地址。 地址不能为 NULL，该变量可以具有任何值。  
  
## <a name="return-value"></a>返回值  
 成功创建提供程序和标记系列时返回 S_OK，出现任何错误时返回错误代码。 使用 SUCCEEDED/FAILED 宏检查错误条件。  
  
## <a name="requirements"></a>惠?  
 **标头：** cvmarkers.h  
  
## <a name="see-also"></a>请参阅  
 [C++ 库参考](../profiling/cpp-library-reference.md)