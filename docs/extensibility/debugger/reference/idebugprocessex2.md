---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e0b29d88387ccb2ed711f1a000bf7bb00a34dd01
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084253"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
此接口允许的会话调试管理器 (SDM) 通知过程将附加到或与进程分离。

## <a name="syntax"></a>语法

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>实施者的说明
 自定义端口提供程序在与相同的对象上实现此接口[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)接口以便：

- 支持跟踪的会话连接到的进程

- 支持自动附加跨多个调试引擎

  如果还选择能自定义端口供应商可以实现此接口。

## <a name="notes-for-callers"></a>调用方的说明

- SDM 调用[QueryInterface](/cpp/atl/queryinterface)上`IDebugProcess2`接口，以获得此接口。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 下表显示的方法`IDebugProcessEx2`。

|方法|描述|
|------------|-----------------|
|[附加](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|通知会话现在正在调试的进程的进程。|
|[分离](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|通知该过程在会话不再调试进程。|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|将添加一系列的调试引擎的程序节点。|

## <a name="remarks"></a>备注
 此接口是专用 SDM 和进程之间。

## <a name="requirements"></a>要求
 标头：Portpriv.h

 命名空间:Microsoft.VisualStudio.Debugger.Interop

 程序集：Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>请参阅
- [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)