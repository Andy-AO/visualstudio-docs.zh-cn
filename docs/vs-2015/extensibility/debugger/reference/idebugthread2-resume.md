---
title: IDebugThread2：： Resume |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5bdec7338864926187b3d5056ffd2f2c4e1d7824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152995"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

继续执行线程。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pdwSuspendCount`  
 弄返回恢复操作后的挂起计数。  
  
## <a name="return-value"></a>返回值  
 如果成功， `S_OK` 则返回; 否则返回错误代码。  
  
## <a name="remarks"></a>备注  
 对此方法的每个调用都将减少挂起计数，直到达到0，此时将实际恢复执行。 此挂起计数显示在 " **线程** 调试" 窗口中。  
  
 对于对此方法的每个调用，必须有对 [挂起](../../../extensibility/debugger/reference/idebugthread2-suspend.md) 方法的以前调用。 "挂起计数" 确定到 `IDebugThread2::Suspend` 目前为止已调用方法的次数。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [挂起](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
