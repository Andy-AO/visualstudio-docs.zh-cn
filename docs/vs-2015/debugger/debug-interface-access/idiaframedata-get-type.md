---
title: IDiaFrameData::get_type | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 95232ab69d6f30435807764e1177d15d6e4622d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161425"
---
# <a name="idiaframedataget_type"></a>IDiaFrameData::get_type
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

检索特定于编译器的帧类型。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pRetVal`  
 弄返回 [StackFrameTypeEnum 枚举](../../debugger/debug-interface-access/stackframetypeenum.md) 枚举中的一个值，该值指示特定于编译器的帧类型。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 `S_OK`。 `S_FALSE`如果此属性不受支持，则返回。 否则，返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [StackFrameTypeEnum 枚举](../../debugger/debug-interface-access/stackframetypeenum.md)
