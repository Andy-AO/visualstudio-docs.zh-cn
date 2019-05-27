---
title: IDebugDisassemblyStream2::GetCodeLocationId |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8aca9231f8b5024199e9ee2bc79cb2d33b31628c
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205014"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
返回特定代码上下文的代码位置标识符。

## <a name="syntax"></a>语法

```cpp
HRESULT GetCodeLocationId( 
   IDebugCodeContext2* pCodeContext,
   UINT64*             puCodeLocationId
);
```

```csharp
int GetCodeLocationId( 
   IDebugCodeContext2 pCodeContext,
   out ulong          puCodeLocationId
);
```

## <a name="parameters"></a>参数
`pCodeContext`\
[in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)对象要转换为标识符。

`puCodeLocationId` [out]返回的代码位置标识符。 请参阅“备注”。

## <a name="return-value"></a>返回值
 如果成功，则返回`S_OK`; 否则为返回错误代码。 返回`E_CODE_CONTEXT_OUT_OF_SCOPE`代码上下文是否有效，但作用域之外。

## <a name="remarks"></a>备注
 代码位置标识符是特定于调试引擎 (DE) 支持反汇编。 此位置标识符由在内部用于 DE 跟踪代码中的位置，通常是地址或某种类型的偏移量。 唯一要求是，如果代码上下文的一个位置小于另一个位置的代码上下文则相应的代码位置标识符的第一个代码上下文也必须是小于第二个代码上下文的代码位置标识符。

 若要检索的代码位置标识符代码上下文，请调用[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)方法。

## <a name="see-also"></a>请参阅
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)