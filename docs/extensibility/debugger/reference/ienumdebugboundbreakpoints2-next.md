---
title: IEnumDebugBoundBreakpoints2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2::Next
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Next
ms.assetid: cb3a249f-2282-4bdc-b6d8-a4ee4bfb8365
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 542acd97b39813633c1207d90217498dd6fa77b4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62867519"
---
# <a name="ienumdebugboundbreakpoints2next"></a>IEnumDebugBoundBreakpoints2::Next
枚举中返回下一组元素。

## <a name="syntax"></a>语法

```cpp
HRESULT Next(
   ULONG                    celt,
   IDebugBoundBreakpoint2** rgelt,
   ULONG*                   pceltFetched
);
```

```csharp
int Next(
   uint                     celt,
   IDebugBoundBreakpoint2[] rgelt,
   ref uint                 pceltFetched
);
```

#### <a name="parameters"></a>参数
 `celt`

 [in]要检索的元素数。 此外可以指定的最大大小`rgelt`数组。

 `rgelt`

 [in、 out]数组[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)要填充的元素。

 `pceltFetched`

 [out]返回中实际返回的元素数目`rgelt`。

## <a name="return-value"></a>返回值
 如果成功，则返回 `S_OK`。 返回`S_FALSE`如果无法返回请求的元素数少于; 否则，返回错误代码。

## <a name="see-also"></a>请参阅
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)