---
title: IDebugProcess3::GetDebugReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetDebugReason
helpviewer_keywords:
- IDebugProcess3::GetDebugReason
ms.assetid: f23fbabc-8b18-4278-bebf-4cdc7091513c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55f49d94ec95af8c7c74205335fe69b1ec3ecd41
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917684"
---
# <a name="idebugprocess3getdebugreason"></a>IDebugProcess3::GetDebugReason
此方法返回的原因进行调试时启动进程。

## <a name="syntax"></a>语法

```cpp
HRESULT GetDebugReason(
   DEBUG_REASON* pReason
);
```

```csharp
int GetDebugReason(
   out enum_DEBUG_REASON pReason
);
```

#### <a name="parameters"></a>参数
 `pReason`

 [out]返回一个值从[DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)枚举。

## <a name="return-value"></a>返回值
 如果成功，则返回`S_OK`; 否则为将返回错误代码。

## <a name="see-also"></a>请参阅
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)