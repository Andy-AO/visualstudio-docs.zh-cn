---
title: IDebugGenericFieldInstance::GetTypeArguments |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTypeArguments
- IDebugGenericFieldInstance::GetTypeArguments
ms.assetid: 6e7e0f95-181a-4805-adb3-c2407de0ab93
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c69c0d71fb2ef80250ac54eab62e15da33959dcb
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200553"
---
# <a name="idebuggenericfieldinstancegettypearguments"></a>IDebugGenericFieldInstance::GetTypeArguments
检索此实例的类型参数参数。

## <a name="syntax"></a>语法

```cpp
HRESULT GetTypeArguments(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   ULONG32*      pcArgs
);
```

```csharp
int GetTypeArguments(
   uint              cArgs,
   out IDebugField[] ppArgs,
   ref uint          pcArgs
);
```

## <a name="parameters"></a>参数
`cArgs`\
[in]类型参数的数目。

`ppArgs`\
[out]返回的类型参数的数组。

`pcArgs`\
[in、 out]中的成员数`ppArgs`数组。

## <a name="return-value"></a>返回值
 如果成功，则返回`S_OK`; 否则为返回错误代码。

## <a name="see-also"></a>请参阅
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)