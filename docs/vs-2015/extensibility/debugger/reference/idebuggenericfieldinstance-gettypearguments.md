---
title: IDebugGenericFieldInstance：： GetTypeArguments |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetTypeArguments
- IDebugGenericFieldInstance::GetTypeArguments
ms.assetid: 6e7e0f95-181a-4805-adb3-c2407de0ab93
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bef4d6c0d36eafd0279d97ecad2d1d2cc0656e2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180820"
---
# <a name="idebuggenericfieldinstancegettypearguments"></a>IDebugGenericFieldInstance::GetTypeArguments
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

检索此实例的类型参数参数。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
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
  
#### <a name="parameters"></a>参数  
 `cArgs`  
 中类型参数的数目。  
  
 `ppArgs`  
 弄返回类型参数的数组。  
  
 `pcArgs`  
 [in，out]数组中的成员数 `ppArgs` 。  
  
## <a name="return-value"></a>返回值  
 如果成功， `S_OK` 则返回; 否则返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
