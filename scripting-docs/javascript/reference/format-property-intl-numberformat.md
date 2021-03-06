---
title: format 属性 (Intl.NumberFormat) |Microsoft 文档
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7528c79852c4836dfd967322b876d738f9781107
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572470"
---
# <a name="format-property-intlnumberformat"></a>format 属性 (Intl.NumberFormat)
返回一个函数，设置特定于区域设置数字格式通过使用指定的数字格式化程序设置。  
  
## <a name="syntax"></a>语法  
  
```  
numberFormatObj.format  
```  
  
#### <a name="parameters"></a>参数  
 `numberFormatObj`  
 必须的。 名称`NumberFormat`要用作格式化程序对象。  
  
## <a name="remarks"></a>备注  
 返回的函数`format`属性采用单个参数， `value`，并返回一个字符串，通过使用中指定的选项表示本地化的数`NumberFormat`对象。 如果`value`未提供，则该函数将返回`NaN`（而不是数字）。  
  
## <a name="example"></a>示例  
 下面的示例使用`NumberFormat`对象来创建本地化的数量。  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigits: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>请参阅  
 [Intl.NumberFormat 对象](../../javascript/reference/intl-numberformat-object-javascript.md)