---
title: 示例表达式计算的实现 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 49fd700120e819bb0b38cb8d91401869a364714c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039448"
---
# <a name="sample-implementation-of-expression-evaluation"></a>表达式计算的实现示例
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种方式实现表达式计算器已弃用。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)并[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 有关**Watch**窗口表达式中，Visual Studio 调用[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)以生成[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)对象。 `IDebugExpressionContext2::ParseText` 实例化的表达式计算器 (EE) 和调用[分析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)来获取[IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)对象。  
  
 此实现`IDebugExpressionEvaluator::Parse`执行下列任务：  
  
1. [C++仅]分析表达式来查找错误。  
  
2. 实例化一个类 (称为`CParsedExpression`在此示例中)，它实现`IDebugParsedExpression`接口，并将存储在类中要分析的表达式。  
  
3. 返回`IDebugParsedExpression`接口从`CParsedExpression`对象。  
  
> [!NOTE]
>  在下面的示例和 MyCEE 示例中，表达式计算器不会将从评估分析。  
  
## <a name="managed-code"></a>托管代码  
 这是一个实现的`IDebugExpressionEvaluator::Parse`在托管代码中。 请注意此版本的方法将推迟到分析[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)用于分析的代码也计算在同一时间 (请参阅[计算监视表达式](../../extensibility/debugger/evaluating-a-watch-expression.md))。  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT Parse(  
                string                 expression,   
                uint                   parseFlags,  
                uint                   radix,  
            out string                 errorMessage,   
            out uint                   errorPosition,   
            out IDebugParsedExpression parsedExpression)  
        {   
            errorMessage = "";  
            errorPosition = 0;  
  
            parsedExpression =  
                new CParsedExpression(parseFlags, radix, expression);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>非托管代码  
 这是一个实现的`IDebugExpressionEvaluator::Parse`非托管代码中。 此方法调用帮助程序函数， `Parse`，以便分析表达式并检查错误，但此方法忽略生成的值。 正式评估将推迟到[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)时其计算结果分析表达式 (请参阅[计算监视表达式](../../extensibility/debugger/evaluating-a-watch-expression.md))。  
  
```cpp#  
STDMETHODIMP CExpressionEvaluator::Parse(  
        in    LPCOLESTR                 pszExpression,  
        in    PARSEFLAGS                flags,  
        in    UINT                      radix,  
        out   BSTR                     *pbstrErrorMessages,  
        inout UINT                     *perrorCount,  
        out   IDebugParsedExpression  **ppparsedExpression  
    )  
{  
    if (pbstrErrorMessages == NULL)  
        return E_INVALIDARG;  
    else  
        *pbstrErrormessages = 0;  
  
    if (pparsedExpression == NULL)  
        return E_INVALIDARG;  
    else  
        *pparsedExpression = 0;  
  
    if (perrorCount == NULL)  
        return E_INVALIDARG;  
  
    HRESULT hr;  
    // Look for errors in the expression but ignore results  
    hr = ::Parse( pszExpression, pbstrErrorMessages );  
    if (hr != S_OK)  
        return hr;  
  
    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );  
    if (!pparsedExpr)  
        return E_OUTOFMEMORY;  
  
    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,  
                                      reinterpret_cast<void**>(ppparsedExpression) );  
    pparsedExpr->Release();  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [计算监视窗口表达式](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [计算监视表达式](../../extensibility/debugger/evaluating-a-watch-expression.md)
