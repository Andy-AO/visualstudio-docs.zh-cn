---
title: IDebugPointerField::GetDereferencedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51ddd954e069ae2f6a683b727305808b8591d4f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872038"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
此方法返回的此指针对象所指向的对象的类型。

## <a name="syntax"></a>语法

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

#### <a name="parameters"></a>参数
 `ppField`

 [out]返回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)描述类型的目标对象。

## <a name="return-value"></a>返回值
 如果成功，则返回`S_OK`; 否则为返回错误代码。

## <a name="remarks"></a>备注
 例如，如果[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)对象指向一个整数， [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)此方法返回的类型描述该整数类型。

## <a name="see-also"></a>请参阅
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)