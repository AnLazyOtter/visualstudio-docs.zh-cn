---
title: "prototype 属性 (Object) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Prototype
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- inheritance, objects
- Prototype property
ms.assetid: 9fc434a1-5995-4fcb-a4e8-00e7f615aaa2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a73d213b6b17f5046eb1f4c498aeb223f942f2d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-object-javascript"></a>prototype 属性（对象）(JavaScript)
为对象的类返回原型的引用。  
  
## <a name="syntax"></a>语法  
  
```  
  
objectName.prototype  
```  
  
## <a name="remarks"></a>备注  
 `objectName` 参数是对象的名称。  
  
 使用 `prototype` 属性，从而向对象的类提供基本功能集。 对象的新实例“继承”了分配给该对象的原型的行为。  
  
 例如，要将方法添加到返回数组的最大元素值的 `Array` 对象，请声明该函数，将其添加至 `Array.prototype`，然后再使用它。  
  
```JavaScript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output:  
// 25  
  
```  
  
 所有内部[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]对象具有`prototype`属性是只读的。 属性和方法可能添加至原型，但该对象可能无法为指定其他原型。 但是，可能将用户定义的对象分配的新原型。  
  
 此语言参考中每个内部函数对象的方法和属性列表指示哪些是属于该对象的原型，哪些不是。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [constructor 属性 (Object)](../../javascript/reference/constructor-property-object-javascript.md)