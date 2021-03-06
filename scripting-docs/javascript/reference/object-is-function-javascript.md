---
title: "Object.is 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 6e2f6c6d-7cd2-47c4-a513-3ba53988d27d
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36d4c281fdafbfacb0b1f6061ef4a90bfac99234
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="objectis-function-javascript"></a>Object.is 函数 (JavaScript)
返回一个值，该值指示两个值是否相同。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
Object.is(value1, value2)  
```  
  
#### <a name="parameters"></a>参数  
 `value1`  
 必需。 要测试的第一个值。  
  
 `value2`  
 必需。 要测试的第二个值。  
  
## <a name="return-value"></a>返回值  
 如果值相同，则为 `true`；否则为 `false`。  
  
## <a name="remarks"></a>备注  
 与 = = 运算符不同，`Object.is` 在测试值时不会强制任何类型。  
  
 `Object.is` 应用的比较类似于 === 运算符所应用的比较，区别在于 `Object.is` 将 `Number.isNaN` 视作与 `NaN` 相同的值。 它还将 + 0 和-0 视作不同值。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]