---
title: FIELD_INFO_FIELDS |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c181d1483dc33e8931436c24fc3cf681d182ab34
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47481554"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主题的最新版本，请参阅[FIELD_INFO_FIELDS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/field-info-fields)。  
  
指定要检索相关信息[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)对象。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## <a name="members"></a>成员  
 FIF_FULLNAME  
 初始化/用`bstrFullName`字段中[FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)结构。  
  
 FIF_NAME  
 初始化/用`bstrName`字段中`FIELD_INFO`结构。  
  
 FIF_TYPE  
 初始化/用`bstrType`字段中`FIELD_INFO`结构。  
  
 FIF_MODIFIERS  
 初始化/用`bstrModifiers`字段中`FIELD_INFO`结构。  
  
## <a name="remarks"></a>备注  
 这些值也会作为参数传递[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)方法，以指定的哪些字段[FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)结构是进行初始化。  
  
 中还使用这些值`dwFields`的成员`FIELD_INFO`结构，用于指示哪些字段是使用，有效。  
  
 可能的按位组合这些标志`OR`。  
  
## <a name="requirements"></a>要求  
 标头： sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
