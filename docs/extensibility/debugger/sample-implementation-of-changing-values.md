---
title: 更改值的实现示例 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, local values
- debugging [Debugging SDK], expression evaluation
ms.assetid: ee2d955b-12ca-4f27-89aa-c2d0e768b6b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39c662af2aa9f1fed2f36aefc60b6b2e539a0200
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="sample-implementation-of-changing-values"></a>更改值的实现示例
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 显示在每个本地**局部变量**窗口具有[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)对象与之关联。 这`IDebugProperty2`对象包含局部变量的名称、 值和类型。 当用户更改本地的值时，Visual Studio 会调用[SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)来更新本地内存中的值。 在此示例中，由表示本地`CFieldProperty`类，该类实现`IDebugProperty2`接口。  
  
> [!NOTE]
>  有关**监视**和**快速监视**正在更改的值由表达式， `CValueProperty` MyCEE 示例中的类。 但是，实现`IDebugProperty2::SetValueAsString`相同如下所示。  
  
 此实现的`IDebugProperty2::SetValueAsString`将执行以下任务：  
  
1.  要生成的值的表达式的计算结果。  
  
2.  将绑定关联[IDebugField](../../extensibility/debugger/reference/idebugfield.md)对象移到其内存位置，并生成[IDebugObject](../../extensibility/debugger/reference/idebugobject.md)对象。  
  
3.  将值转换为一系列字节。  
  
4.  调用[SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md)来在内存中存储的字节。  
  
## <a name="managed-code"></a>托管代码  
 这是实现`IDebugProperty2::SetValueAsString`在托管代码中。  
  
```  
[C#]  
namespace EEMC  
{  
    public class CFieldProperty : IDebugProperty2  
    {  
        public HRESULT SetValueAsString(  
            string pszValue,  
            uint   dwRadix,  
            uint   dwTimeout)  
        {  
            HRESULT hr = COM.E_NOTIMPL;  
            uint flags = (uint)enum_PARSEFLAGS.PARSE_EXPRESSION;  
            CParsedExpression parsedExpression =  
                new CParsedExpression(flags, dwRadix, pszValue);  
            IDebugProperty2 value;  
            parsedExpression.EvaluateSync(flags,  
                                          dwTimeout,  
                                          null,  
                                          null,  
                                          null,  
                                          "string",  
                                          out value);  
            if (value != null)  
            {  
                DEBUG_PROPERTY_INFO[] dpi = new DEBUG_PROPERTY_INFO[1];  
                hr = value.GetPropertyInfo(  
                    (uint)enum_DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_VALUE,  
                    dwRadix,  
                    dwTimeout,  
                    null,  
                    0,  
                    dpi);  
                if (hr == COM.S_OK)  
                {  
                    hr = Field.SetValue(binder,  
                                        field,  
                                        dpi[0].bstrValue);  
                }  
            }  
            return hr;  
        }  
    }  
  
//----------------------------------------------------------------------------  
  
    internal class Field  
    {  
        internal static HRESULT SetValue(  
            IDebugBinder binder,  
            IDebugField  field,  
            string       bstrValue)  
        {  
            HRESULT hr = COM.E_FAIL;  
            uint fieldSize = 0;  
            Type fieldType = GetType(field, out fieldSize);  
            if (fieldType != null)  
            {  
                FIELD_INFO[] fi = new FIELD_INFO[1];  
                hr = field.GetInfo((uint)enum_FIELD_INFO_FIELDS.FIF_MODIFIERS, fi);  
                if (hr != COM.S_OK ||  
                   (fi[0].dwModifiers & (uint)enum_FIELD_MODIFIERS.FIELD_MOD_CONSTANT) != 0)  
                {  
                    // Couldn't get field info or field is constant and can't be changed.  
                    return COM.E_FAIL;  
                }  
                IDebugObject valueObject;  
                IntPtr pBuffer = new IntPtr();  
                int bufferSize = 0;  
                binder.Bind(null, field, out valueObject);  
                if (valueObject != null)  
                {  
                    if (fieldType == typeof(sbyte))  
                    {  
                        sbyte value = Convert.ToSByte(bstrValue);  
                        bufferSize = 1;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(short))  
                    {  
                        System.Int16 value = Convert.ToInt16(bstrValue);  
                        bufferSize = 2;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(int))  
                    {  
                        System.Int32 value = Convert.ToInt32(bstrValue);  
                        bufferSize = 4;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(long))  
                    {  
                        System.Int64 value = Convert.ToInt64(bstrValue);  
                        bufferSize = 8;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(byte))  
                    {  
                        byte value = Convert.ToByte(bstrValue);  
                        bufferSize = 1;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(char))  
                    {  
                        char value = Convert.ToChar(bstrValue);  
                        bufferSize = 1;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(bool))  
                    {  
                        bool value = Convert.ToBoolean(bstrValue);  
                        bufferSize = 1;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(uint))  
                    {  
                        System.UInt32 value = Convert.ToUInt32(bstrValue);  
                        bufferSize = 4;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                   if (fieldType == typeof(ulong))  
                   {  
                        System.UInt64 value = Convert.ToUInt64(bstrValue);  
                        bufferSize = 8;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                   }  
  
                   if (fieldType == typeof(float))  
                   {  
                        float value = Convert.ToSingle(bstrValue);  
                        bufferSize = sizeof(float);  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                   }  
  
                   if (fieldType == typeof(double))  
                   {  
                        double value = Convert.ToDouble(bstrValue);  
                        bufferSize = sizeof(double);  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                   }  
  
                   if (fieldType == typeof(string))  
                   {  
                        bufferSize = bstrValue.Length;  
                        pBuffer = Marshal.StringToCoTaskMemAuto(bstrValue);  
                   }  
                   if (bufferSize != 0)  
                   {  
                        byte[] byteBuffer = new byte[bufferSize];  
                        for (int i = 0; i < bufferSize; i++)  
                        {  
                            byteBuffer[i] = Marshal.ReadByte(pBuffer,i);  
                        }  
                        Marshal.FreeCoTaskMem(pBuffer);  
                        hr = valueObject.SetValue(byteBuffer, (uint)bufferSize);  
                    }  
                }  
            }  
            return hr;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>非托管代码  
 这是实现`IDebugProperty2::SetValueAsString`在托管代码中。 Helper 函数`FieldCoerceValueType`（未显示）） 强制`VARIANT`为特定类型并可确保的值是一个类型`FieldSetValue`可以处理。  
  
```  
[C++]  
STDMETHODIMP CFieldProperty::SetValueAsString(   
        in LPCOLESTR pszValueStr,  
        in DWORD     radix,  
        in DWORD     timeout  
        )  
{  
    HRESULT hr;  
  
    //evaluate the value  
    VARIANT value;  
    hr = Evaluate( m_provider,  
                   m_address,  
                   m_binder,  
                   pszValueStr,  
                   NULL,  
                   &value );  
    if (FAILED(hr))  
        return hr;  
    if (hr == S_FALSE)  
        return E_FAIL;   //parse failed  
  
    //copy the bits  
    hr = FieldSetValue( m_binder, m_field, value );  
  
    return hr;  
}  
  
//----------------------------------------------------------------------------  
  
HRESULT FieldSetValue(  
        in IDebugBinder* pbinder,  
        in IDebugField*  pfield,  
        in VARIANT&      rawValue )  
{  
    if (pfield == NULL)  
        return E_INVALIDARG;  
  
    if (pbinder == NULL)  
        return E_INVALIDARG;  
  
    HRESULT       hr      = S_OK;  
    IDebugObject* pobject = NULL;  
    VARIANT       value;  
    VariantInit(&value);  
  
    //check the type  
    hr = FieldCoerceValueType( pbinder, pfield, rawValue, &value );  
    if (FAILED(hr))  
        goto fail;  
    if (hr == S_FALSE)  
    {  
        VariantClear(value);  
        return E_FAIL;  
    }  
  
    //get the object  
    hr = pbinder->Bind( NULL, pfield, &pobject );  
    if (FAILED(hr))  
    {  
        pobject->Release();  
        VariantClear(value);  
        return hr;  
    }  
  
    //set the value  
    switch (value.vt)  
    {  
        case VT_BSTR:  
        {  
            if (value.bstrVal == NULL)  
            {  
                LPOLESTR pszEmptyStr = OLE("");  
                hr = pobject->SetValue( reinterpret_cast<BYTE*>(pszEmptyStr),  
                     sizeof(OLECHAR) );  
            }  
            else  
                hr = pobject->SetValue( reinterpret_cast<BYTE*>(value.bstrVal),  
                    (SysStringLen(value.bstrVal)+1) * sizeof(wchar_t));  
        }  
  
        case VT_BOOL:  
        case VT_I1:  
        case VT_UI1:  
            hr = pobject->SetValue( reinterpret_cast<BYTE*>(&(value.byref)), 1 );  
            break;  
  
        case VT_I2:  
        case VT_UI2:  
            hr = pobject->SetValue( reinterpret_cast<BYTE*>(&(value.byref)), 2 );  
            break;  
  
        case VT_I4:  
        case VT_UI4:  
        case VT_R4:  
            hr = pobject->SetValue( reinterpret_cast<BYTE*>(&(value.byref)), 4 );  
            break;  
  
        case VT_I8:  
        case VT_UI8:  
        case VT_R8:  
            hr = pobject->SetValue( reinterpret_cast<BYTE*>(&(value.byref)), 8 );  
            break;  
  
        case VT_VOID:  
        case VT_EMPTY:  
            hr = E_FAIL;  
            break;  
  
        case VT_UNKNOWN:  
        {  
            //this is also a field (structured type)  
            if (value.punkVal == NULL)  
            {  
                pobject->Release();  
                VariantClear(value);  
                return E_FAIL;  
            };  
  
            IDebugField* valueField;  
            hr = value.punkVal->QueryInterface( IID_IDebugField,  
                reinterpret_cast<void**>(&valueField) );  
            if (FAILED(hr))  
            {  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            };  
  
            //for MyC we simply copy the bits  
            IDebugObject* valueObject;  
            hr = pbinder->Bind( NULL, valueField, &valueObject );  
            valueField->Release();  
            if (FAILED(hr))  
            {  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            };  
  
            BYTE* pvalueBits;  
            UINT  valueSize;  
            hr = valueObject->GetSize( &valueSize );  
            if (FAILED(hr))  
            {  
                valueObject->Release();  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            };  
  
            pvalueBits = NALLOC(BYTE,valueSize+1);  
            if (!pvalueBits)  
            {  
                valueObject->Release();  
                pobject->Release();  
                VariantClear(value);  
                return E_OUTOFMEMORY;  
            };  
  
            hr = valueObject->GetValue( pvalueBits, valueSize );  
            valueObject->Release();  
            if (FAILED(hr))  
            {  
                free(pvalueBits);  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            }  
  
            hr = pobject->SetValue( pvalueBits, valueSize );  
            free(pvalueBits);  
            if (FAILED(hr))  
            {  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            }  
  
            break;  
        }  
  
        default:  
            //not a primitive type  
            hr = E_FAIL;  
            break;  
    }  
  
    VariantClear( &value );  
    pobject->Release();  
    return hr;  
}  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [更改本地的值](../../extensibility/debugger/changing-the-value-of-a-local.md)   
 [计算上下文](../../extensibility/debugger/evaluation-context.md)