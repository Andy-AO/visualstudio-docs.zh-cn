---
title: WriteCodeFragment 任务 | Microsoft Docs
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
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa9882d30a8483937f77da21bb4700d4899a68a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555473"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment 任务
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

根据指定的生成代码片段，生成临时代码文件。 不会删除该文件。  
  
## <a name="parameters"></a>参数  
 下表描述了 `WriteCodeFragment` 任务的参数。  
  
|参数|说明|  
|---------------|-----------------|  
|`AssemblyAttributes`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 要编写的属性的说明。 项目 `Include` 值是属性的完整类型名称，例如“System.AssemblyVersionAttribute”。<br /><br /> 每个元数据都是参数的名称/值对，必须为类型 `String`。 某些属性只允许使用位置构造函数参数。 但可在任何属性中使用这些参数。 若要设置位置构造函数属性，请使用类似于“_Parameter1”、“_Parameter2”等元数据名称。<br /><br /> 不能跳过参数索引。|  
|`Language`|必选 `String` 参数。<br /><br /> 指定要生成的代码的语言。<br /><br /> `Language` 可以是任何可用于 CodeDom 提供程序的语言，例如“C#”或“VisualBasic”。 发出的文件将具有该语言的默认文件扩展名。|  
|`OutputDirectory`|可选 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 指定生成代码的目标文件夹，通常为中间文件夹。|  
|`OutputFile`|可选 <xref:Microsoft.Build.Framework.ITaskItem> 输出参数。<br /><br /> 指定已生成文件的路径。 如果使用文件名设置此参数，则会将目标文件夹附加在文件名前。 如果使用根设置，则会忽略目标文件夹。<br /><br /> 如果未设置此参数，输出文件名将为目标文件夹、任意文件名称和指定语言的默认文件扩展名。|  
  
## <a name="remarks"></a>备注  
 除了具有表中列出的参数外，此任务还将从本身继承自 <xref:Microsoft.Build.Utilities.Task> 类的 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数。 有关这些其他参数及其说明的列表，请参阅 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另请参阅  
 [操作](../msbuild/msbuild-tasks.md)   
 [任务引用](../msbuild/msbuild-task-reference.md)
