---
title: IDebugMemoryContext2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f04000d3e2675f766ae343836320aa7433ade87d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211992"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
比较在比较标志，返回与匹配的第一个上下文的索引所指示的方式中的给定数组中每个上下文的内存上下文。

## <a name="syntax"></a>语法

```cpp
HRESULT Compare( 
   CONTEXT_COMPARE        compare,
   IDebugMemoryContext2** rgpMemoryContextSet,
   DWORD                  dwMemoryContextSetLen,
   DWORD*                 pdwMemoryContext
);
```

```csharp
int Compare(
   enum_CONTEXT_COMPARE   compare,
   IDebugMemoryContext2[] rgpMemoryContextSet,
   uint                   dwMemoryContextSetLen,
   out uint               pdwMemoryContext
);
```

## <a name="parameters"></a>参数
`compare`\
[in]中的值[CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)确定比较类型的枚举。

`rgpMemoryContextSet`\
[in]对引用的数组[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)对象进行比较。

`dwMemoryContextSetLen`\
[in]中的环境数`rgpMemoryContextSet`数组。

`pdwMemoryContext`\
[out]返回满足的比较的第一个内存上下文的索引。

## <a name="return-value"></a>返回值
 如果成功，则返回`S_OK`; 否则为返回错误代码。 返回`E_COMPARE_CANNOT_COMPARE`如果不能比较两个上下文。

## <a name="remarks"></a>备注
 调试引擎 (DE) 不需要支持所有类型的比较，但它必须都支持至少`CONTEXT_EQUAL`， `CONTEXT_LESS_THAN`，`CONTEXT_GREATER_THAN`和`CONTEXT_SAME_SCOPE`。

## <a name="see-also"></a>请参阅
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)