---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aed4d652a300ac9b18d45456c56a0b9b56285206
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917106"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
使调试引擎能够重写的默认行为[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 时结束调试会话。

## <a name="syntax"></a>语法

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>实施者的说明
 此接口由的调试引擎实现。 它可用于主机可能会创建和销毁进程的生存期内的多个程序。

## <a name="methods"></a>方法
 下表显示的方法`IDebugProgramDestroyEventFlags2`。

|方法|描述|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|检索程序销毁标志。|

## <a name="remarks"></a>备注
 默认行为[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 是以返回到设计模式下，所有程序具有都发送程序后销毁事件。 此接口使调试引擎，若要更改该行为。

## <a name="requirements"></a>要求
 标头：Msdbg.h

 命名空间:Microsoft.VisualStudio.Debugger.Interop

 程序集：Microsoft.VisualStudio.Debugger.Interop.dll