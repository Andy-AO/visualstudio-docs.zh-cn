---
title: IDebugThread2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4da4f3287d8d307dd65aff5d09aa34c5b17b0119
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199658"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
获取线程的名称。

## <a name="syntax"></a>语法

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>参数
`pbstrName`\
[out]返回线程的名称。

## <a name="return-value"></a>返回值
 如果成功，则返回`S_OK`; 否则为返回错误代码。

## <a name="remarks"></a>备注
 检索到的名称始终是可显示的名称，此名称描述该线程。 线程名称可能派生自的运行时体系结构支持命名的线程，也可能被派生自的调试引擎的名称。 或者，可以通过调用设置线程名称[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)方法。

## <a name="see-also"></a>请参阅
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)