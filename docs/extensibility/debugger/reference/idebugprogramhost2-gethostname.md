---
title: IDebugProgramHost2::GetHostName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 45919c6c9fafceecca2cb53fa9c2c9f43b68e382
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870001"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
获取标题、 友好名称或此程序的宿主进程的文件名。

## <a name="syntax"></a>语法

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

#### <a name="parameters"></a>参数
 `dwType`

 [in]中的值[GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)枚举。

 `pbstrHostName`

 [out]返回宿主进程的请求的名称。

## <a name="return-value"></a>返回值
 如果成功，则返回`S_OK`; 否则为返回错误代码。

## <a name="remarks"></a>备注
 在此方法的典型实现`dwType`忽略参数和返回主机计算机的友好名称。 另一个可能的实现是传递`dwType`的调用的参数[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)方法获取的名称。

## <a name="see-also"></a>请参阅
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)