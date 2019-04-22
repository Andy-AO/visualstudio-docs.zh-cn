---
title: ResolveKeySource 任务 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd5cbe2f4998ab78ce39cde4b26a38b13c70b2f8
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649286"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource 任务
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

确定强名称密钥源。  
  
## <a name="task-parameters"></a>任务参数  
 下表描述了 `ResolveKeySource` 任务的参数。  
  
|参数|说明|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|可选 `Int32` 参数。<br /><br /> 获取或设置显示倒计时消息的时间长度（以秒为单位）。|  
|`AutoClosePasswordPromptTimeout`|可选 `Int32` 参数。<br /><br /> 获取或设置在关闭密码提示对话框之前要等待的时间量（以秒为单位）。|  
|`CertificateFile`|可选 `String` 参数。<br /><br /> 获取或设置证书文件的路径。|  
|`CertificateThumbprint`|可选 `String` 参数。<br /><br /> 获取或设置证书指纹。|  
|`KeyFile`|可选 `String` 参数。<br /><br /> 获取或设置密钥文件的路径。|  
|`ResolvedKeyContainer`|可选 `String` 输出参数。<br /><br /> 获取或设置已解析的密钥容器。|  
|`ResolvedKeyFile`|可选 `String` 输出参数。<br /><br /> 获取或设置已解析的密钥文件。|  
|`ResolvedThumbprint`|可选 `String` 输出参数。<br /><br /> 获取或设置解析的证书指纹。|  
|`ShowImportDialogDespitePreviousFailures`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则无论以前失败与否，均显示导入对话框。|  
|`SuppressAutoClosePasswordPrompt`|可选 `Boolean` 参数。<br /><br /> 获取或设置一个布尔值，该值指定密码提示对话框是否不应该自动关闭。|  
  
## <a name="remarks"></a>备注  
 除上面列出的参数外，此任务还从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，后者自身继承自 <xref:Microsoft.Build.Utilities.Task> 类。 有关这些其他参数的列表及其说明的信息，请参阅 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)
