---
title: IDiaLoadCallback2::RestrictSystemRootAccess | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictSystemRootAccess method
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4a603936f58df37cd54bc32e7b4ea8e35838aa7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62539115"
---
# <a name="idialoadcallback2restrictsystemrootaccess"></a>IDiaLoadCallback2::RestrictSystemRootAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

确定是否在系统根目录下允许搜索.pdb 文件。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT RestrictSystemRootAccess();  
```  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 以外的任何返回代码`S_OK`阻止搜索.pdb 文件系统根目录。  
  
## <a name="see-also"></a>请参阅  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
