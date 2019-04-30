---
title: IDebugBreakpointErrorEvent2::GetErrorBreakpoint |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
helpviewer_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
ms.assetid: e5acfd19-ac17-47f3-a31a-b2aa8baca36d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 362cacab9317aef05cb16e7d9d3e3796439af8af
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923316"
---
# <a name="idebugbreakpointerrorevent2geterrorbreakpoint"></a>IDebugBreakpointErrorEvent2::GetErrorBreakpoint
获取[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)对象，它介绍了为什么未绑定断点的原因。

## <a name="syntax"></a>语法

```cpp
HRESULT GetErrorBreakpoint( 
    IDebugErrorBreakpoint2** ppErrorBP
);
```

```csharp
int GetErrorBreakpoint( 
    out IDebugErrorBreakpoint2 ppErrorBP
);
```

#### <a name="parameters"></a>参数
`ppErrorBP`

 [out]返回[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)描述警告或错误的对象。

## <a name="return-value"></a>返回值
如果成功，则返回`S_OK`; 否则为返回错误代码。

## <a name="remarks"></a>备注
之后`IDebugErrorBreakpoint2`获取接口，请调用[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)方法以获取[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)对象。 然后[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)方法可以用于确定了无效的位置、 无效的表达式或为何挂起断点未绑定，例如，未加载的代码的原因和其他操作。

## <a name="example"></a>示例
下面的示例演示如何实现此方法对于**CBreakpointSetDebugEventBase**对象，它公开[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)接口。

```cpp
STDMETHODIMP CBreakpointErrorDebugEventBase::GetErrorBreakpoint(
    IDebugErrorBreakpoint2 **ppbp)
{
    HRESULT hRes = E_FAIL;

    if ( ppbp )
    {
        if ( m_pError )
        {
            *ppbp = m_pError;

            m_pError->AddRef();

            hRes = S_OK;
        }
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>请参阅
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
