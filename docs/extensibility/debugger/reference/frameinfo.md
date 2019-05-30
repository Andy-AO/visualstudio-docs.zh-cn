---
title: FRAMEINFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1209036bced88cffb3681be0ceedd28942714419
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344464"
---
# <a name="frameinfo"></a>FRAMEINFO
描述一个堆栈帧。

## <a name="syntax"></a>语法

```cpp
typedef struct tagFRAMEINFO {
    FRAMEINFO_FLAGS    m_dwValidFields;
    BSTR               m_bstrFuncName;
    BSTR               m_bstrReturnType;
    BSTR               m_bstrArgs;
    BSTR               m_bstrLanguage;
    BSTR               m_bstrModule;
    UINT64             m_addrMin;
    UINT64             m_addrMax;
    IDebugStackFrame2* m_pFrame;
    IDebugModule2*     m_pModule;
    BOOL               m_fHasDebugInfo;
    BOOL               m_fStaleCode;
    BOOL               m_fAnnotatedFrame;
} FRAMEINFO;
```

```csharp
public struct FRAMEINFO {
    public uint              m_dwValidFields;
    public string            m_bstrFuncName;
    public string            m_bstrReturnType;
    public string            m_bstrArgs;
    public string            m_bstrLanguage;
    public string            m_bstrModule;
    public ulong             m_addrMin;
    public ulong             m_addrMax;
    public IDebugStackFrame2 m_pFrame;
    public IDebugModule2     m_pModule;
    public int               m_fHasDebugInfo;
    public int               m_fStaleCode;
    public int               m_fAnnotatedFrame;
} FRAMEINFO;
```

## <a name="members"></a>成员
`m_dwValidFields`\
中的标志的组合[FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)枚举，用于指定哪些字段填充。

`m_bstrFuncName`\
与此堆栈帧关联的函数名称。

`m_bstrReturnType`\
与此堆栈帧关联的返回类型。

`m_bstrArgs`\
与此堆栈帧关联的函数的参数。

`m_bstrLanguage`\
在其中实现该函数使用的语言。

`m_bstrModule`\
与此堆栈帧关联的模块名称。

`m_addrMin`\
最小物理堆栈地址中。

`m_addrMAX`\
最大物理堆栈地址中。

`m_pFrame`\
[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)对象，表示此堆栈帧。

`m_pFrame`\
[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)对象，表示包含此堆栈帧的模块。

`m_fHasDebugInfo`\
非零 (`TRUE`) 如果给定范围中存在的调试信息。

`m_fHasDebugInfo`\
非零 (`TRUE`) 将不再有效的代码与关联的堆栈帧时。

`m_fHasDebugInfo`\
非零 (`TRUE`) 如果会话调试管理器 (SDM) 进行批注的堆栈帧。

## <a name="remarks"></a>备注
此结构传递给[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)要填充的方法。 此结构也包含在一个列表，其中包含在[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)接口，反过来，通过调用将返回该值[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)方法。

## <a name="requirements"></a>要求
标头： msdbg.h

命名空间:Microsoft.VisualStudio.Debugger.Interop

程序集：Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>请参阅
- [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
