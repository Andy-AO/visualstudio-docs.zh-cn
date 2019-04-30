---
title: IDebugClassField::EnumConstructors |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ecc2e2fba9dbddc12a58866c7edcde51b148af1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922695"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
创建此类的构造函数的枚举器。

## <a name="syntax"></a>语法

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

#### <a name="parameters"></a>参数
 `cMatch`

 [in]中的值[CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)枚举，用于指定构造函数来枚举的类型。

 `ppEnum`

 [out]返回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)对象，表示构造函数的列表。 如果没有的构造函数，则返回 null 值。

## <a name="return-value"></a>返回值
 如果成功，则返回 S_OK 或如果没有的构造函数，则返回 S_FALSE。 否则，返回错误代码。

## <a name="remarks"></a>备注
 枚举每个元素均[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)描述构造函数方法的对象。

 通常，构造函数的列表不包括由编译器提供的默认构造函数。

## <a name="see-also"></a>请参阅
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)