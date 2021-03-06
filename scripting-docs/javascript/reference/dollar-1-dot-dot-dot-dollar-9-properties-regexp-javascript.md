---
title: "$1...$9 属性 (RegExp) (JavaScript) |Microsoft 文档"
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
- $1...$9
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- $1...$9 properties
ms.assetid: 8bd84851-f62f-4eb1-a93d-b67135ea091a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1926d6281c9003c432c9c9e89a73a48a584ef4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="19-properties-regexp-javascript"></a>$1...$9 属性 (RegExp) (JavaScript)
返回最近所存储的九个模式匹配过程中找到的部分。 只读。  
  
## <a name="syntax"></a>语法  
  
```  
  
RegExp.$n   
```  
  
## <a name="parameters"></a>参数  
 `RegExp`  
 始终全局`RegExp`对象。  
  
 `n`  
 任何从 1 到 9 的整数。  
  
## <a name="remarks"></a>备注  
 值**$1...$9**只要成功用圆括号括起来匹配，就会修改属性。 可能在正则表达式模式中，指定任意数量的用圆括号括起来子字符串，但可以存储仅的九个的最新。  
  
## <a name="example"></a>示例  
 下面的示例执行正则表达式搜索。 它显示匹配项，并从全局 submatches`RegExp`对象。 子匹配项是成功用圆括号括起来的匹配项中包含`$1...$9`属性。 此示例还显示匹配项，并从返回的数组 submatches`exec`方法。  
  
```JavaScript  
var newLine = "<br />";  
  
var re = /(\w+)@(\w+)\.(\w+)/g  
var src = "Please send mail to george@contoso.com and someone@example.com. Thanks!"  
  
var result;  
var s = "";  
  
// Get the first match.  
result = re.exec(src);  
  
while (result != null) {  
    // Show the entire match.  
    s += newLine;  
  
    // Show the match and submatches from the RegExp global object.  
    s += "RegExp.lastMatch: " + RegExp.lastMatch + newLine;  
    s += "RegExp.$1: " + RegExp.$1 + newLine;  
    s += "RegExp.$2: " + RegExp.$2 + newLine;  
    s += "RegExp.$3: " + RegExp.$3 + newLine;  
  
    // Show the match and submatches from the array that is returned  
    // by the exec method.  
    for (var index = 0; index < result.length; index++) {  
        s +=  index + ": ";  
        s += result[index];  
        s += newLine;  
    }  
  
    // Get the next match.  
    result = re.exec(src);  
}  
document.write(s);  
  
// Output:  
//  RegExp.lastMatch: george@contoso.com  
//  RegExp.$1: george  
//  RegExp.$2: contoso  
//  RegExp.$3: com  
//  0: george@contoso.com  
//  1: george  
//  2: contoso  
//  3: com  
  
//  RegExp.lastMatch: someone@example.com  
//  RegExp.$1: someone  
//  RegExp.$2: example  
//  RegExp.$3: com  
//  0: someone@example.com  
//  1: someone  
//  2: example  
//  3: com  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**: [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)