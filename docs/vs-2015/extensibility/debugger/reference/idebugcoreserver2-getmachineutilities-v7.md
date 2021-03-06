---
title: IDebugCoreServer2：： GetMachineUtilities_V7 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 131f5a5f276b3f93d2ede3d088556b6832cc3651
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840772"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此方法获取服务器的计算机实用程序。  
  
> [!NOTE]
> 此方法已过时： [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] `E_NOTIMPL` 如果) 调用此方法，请不要使用 (总是返回。 由于历史原因，将保留它。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>parameters  
 `ppUtil`  
 弄返回 `IDebugMDMUtil2_V7` 表示计算机实用工具信息的接口。  
  
## <a name="return-value"></a>返回值  
 始终返回 `E_NOTIMPL` ，指示未实现该方法。  
  
## <a name="remarks"></a>备注  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]`E_NOTIMPL`如果调用此方法，则始终返回。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
