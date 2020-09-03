---
title: Error 任务 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b220d12b872a81cba5f46bd14fdebafaa58cf4a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201811"
---
# <a name="error-task"></a>Error 任务
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

基于评估的条件语句，停止生成操作并记录错误。  
  
## <a name="parameters"></a>参数  
 下表描述了 `Error` 任务的参数。  
  
|参数|描述|  
|---------------|-----------------|  
|`Code`|可选 `String` 参数。<br /><br /> 与错误关联的错误代码。|  
|`File`|可选 `String` 参数。<br /><br /> 包含错误的文件的名称。 如果未提供任何文件名称，将使用包含 Error 任务的文件。|  
|`HelpKeyword`|可选 `String` 参数。<br /><br /> 与错误关联的 Help 关键字。|  
|`Text`|可选 `String` 参数。<br /><br /> `Condition` 参数评估为 `true` 时 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 记录的错误文本。|  
  
## <a name="remarks"></a>备注  
 `Error` 任务允许 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 项目将错误文本上报给记录器并停止执行生成。  
  
 如果 `Condition` 参数评估为 `true`，将停止生成，并记录一个错误。 如果 `Condition` 参数不存在，将记录错误并停止执行生成。 有关日志记录的详细信息，请参阅 [获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)。  
  
 除上面列出的参数外，此任务还从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，后者自身继承自 <xref:Microsoft.Build.Utilities.Task> 类。 有关这些其他参数及其说明的列表，请参阅 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>示例  
 以下代码示例验证所有所需的属性均得以设置。 如果未设置这些属性，则项目引发错误事件，并记录 `Error` 任务中 `Text` 参数的值。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>另请参阅  
 [任务引用](../msbuild/msbuild-task-reference.md)   
 [获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)
