---
title: IEnumDebugCustomAttributes |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3c93bde1395a1eec960085c640463e70dee3397
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65225854"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
枚举的自定义特性。

## <a name="syntax"></a>语法

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>实施者的说明
 符号提供程序实现此接口以支持自定义属性 (通过[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)接口)。

## <a name="notes-for-callers"></a>调用方的说明
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)返回此接口。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 下表显示的方法`IEnumDebugCustomAttributes`。

|方法|描述|
|------------|-----------------|
|[下一页](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|检索指定的数目的枚举序列中的自定义属性。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|跳过枚举序列中的自定义属性的指定的数目。|
|[Reset](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|将枚举序列重置到开头。|
|[Clone](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|创建一个包含当前枚举数形式的相同枚举状态的枚举器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|获取一个枚举器中的自定义属性的数目。|

## <a name="requirements"></a>要求
 标头： sh.h

 命名空间:Microsoft.VisualStudio.Debugger.Interop

 程序集：Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>请参阅
- [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)