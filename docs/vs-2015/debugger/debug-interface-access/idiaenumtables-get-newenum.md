---
title: IDiaEnumTables::get__NewEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::get__NewEnum method
ms.assetid: 7b1159c7-a5f0-4baa-861a-dc11437d8b93
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 04450a5c4be636c29a645cda0523cc910ab8b80f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202603"
---
# <a name="idiaenumtablesget__newenum"></a>IDiaEnumTables::get__NewEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

检索 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 此枚举器的版本。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pRetVal`  
 弄返回 `IUnknown` 一个接口，该接口表示 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 此枚举器的版本。  
  
## <a name="return-value"></a>返回值  
 如果成功， `S_OK` 则返回; 否则返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
