---
title: EXCEPTION_INFO |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c48772ed5835daeff9d47773e6e48526993fa425
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
描述的异常或由正在调试的程序引发的运行时错误。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>成员  
 pProgram  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)表示发生了异常的程序的对象。  
  
 bstrProgramName  
 发生了异常的程序名称。  
  
 bstrExceptionName  
 异常的名称。  
  
 dwCode  
 异常或运行时错误标识代码。  
  
 dwState  
 取值范围为[EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)定义异常状态的枚举。  
  
 guidType  
 GUID 语言标识符，`guidLang`或`guidEng`。  
  
## <a name="remarks"></a>备注  
 此结构传递作为参数传递给[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)和[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)方法。 此结构还传递给[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)方法填充的。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)