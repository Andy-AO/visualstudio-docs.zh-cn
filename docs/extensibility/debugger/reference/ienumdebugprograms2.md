---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a37ad954202910930ff06c8206e66c0594a8d1d8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107393"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
此接口枚举当前调试会话中运行的程序。

## <a name="syntax"></a>语法

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>实施者的说明
 调试引擎 (DE) 实现此接口以提供 DE 正在调试的程序的列表。

## <a name="notes-for-callers"></a>调用方的说明
 Visual Studio 调用[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)若要获取此接口。 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)不由 Visual Studio。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 下表显示的方法`IEnumDebugPrograms2`。

|方法|描述|
|------------|-----------------|
|[下一页](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|检索指定的数目的枚举序列中的程序。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|将跳过指定的数目的枚举序列中的程序。|
|[Reset](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|将枚举序列重置到开头。|
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|创建一个包含当前枚举数形式的相同枚举状态的枚举器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|获取一个枚举器中的程序的数量。|

## <a name="remarks"></a>备注
 Visual Studio 将使用此接口：

- 填充**模块**窗口 (通过调用[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) ，然后再调用[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)上每个程序)。

- 填充**附加到进程**列表 (通过调用`IDebugProcess2::EnumPrograms`，然后再调用[QueryInterface](/cpp/atl/queryinterface)上每个[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)接口，以获得[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)接口)。

- 生成一系列可以调试过程中的每个程序的 DEs (使用[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md))。

- 将编辑并继续 (ENC) 更新应用于每个程序 (通过调用 IDebugProcess2::EnumPrograms 然后调用[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md))。

## <a name="requirements"></a>要求
 标头： msdbg.h

 命名空间:Microsoft.VisualStudio.Debugger.Interop

 程序集：Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>请参阅
- [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)