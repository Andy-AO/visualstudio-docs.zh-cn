---
title: IDebugBinder3::GetMemoryObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetMemoryObject
helpviewer_keywords:
- IDebugBinder3::GetMemoryObject method
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7741ad4f7b587cbd31888e643557c744ca4200e2
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2019
ms.locfileid: "65614970"
---
# <a name="idebugbinder3getmemoryobject"></a>IDebugBinder3::GetMemoryObject
此方法检索表示此对象绑定到的内存的内存对象。

## <a name="syntax"></a>语法

```cpp
HRESULT GetMemoryObject(
   IDebugField*   pField,
   UINT64         uConstant,
   IDebugObject** ppObject
);
```

```csharp
int GetMemoryObject(
   IDebugField      pField,
   long             uConstant,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>参数
`pField`\
[in]指定要获取的内存对象的字段。

`uConstant`\
[in]表示内存地址或值的常量值。

`ppObject`\
[out][IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)表示此对象绑定到的内存。

## <a name="return-value"></a>返回值
 如果成功，则返回`S_OK`; 否则为返回错误代码。

## <a name="see-also"></a>请参阅
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)