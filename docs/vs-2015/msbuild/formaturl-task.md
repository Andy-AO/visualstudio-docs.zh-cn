---
title: FormatUrl 任务 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bb870bcc3c4297d5d1b403176f931f75e418d423
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59651470"
---
# <a name="formaturl-task"></a>FormatUrl 任务
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

将 URL 转换为正确的 URL 格式。  
  
## <a name="parameters"></a>参数  
 下表描述了 `FormatUrl` 任务的参数。  
  
|参数|说明|  
|---------------|-----------------|  
|`InputUrl`|可选 `String` 参数。<br /><br /> 指定要格式化的 URL。|  
|`OutputUrl`|可选 `String` 输出参数。<br /><br /> 指定已格式化的 URL。|  
  
## <a name="remarks"></a>备注  
 除具有表中列出的参数外，此任务还从本身继承自 <xref:Microsoft.Build.Utilities.Task> 类的 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数。 有关这些其他参数的列表及其说明的信息，请参阅 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)
