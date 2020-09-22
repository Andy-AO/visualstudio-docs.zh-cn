---
title: MSBuild 任务 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2349c21d55c20bcb3bcd50ab96f383a9afcc00b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840748"
---
# <a name="msbuild-task"></a>MSBuild 任务
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

从另一 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 项目生成 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 项目。  
  
## <a name="parameters"></a>参数  
 下表描述了 `MSBuild` 任务的参数。  
  
|参数|描述|  
|---------------|-----------------|  
|`BuildInParallel`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，会并行生成 `Projects` 参数中指定的项目（如有可能）。 默认值为 `false`。|  
|`Projects`|必选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定要生成的项目文件。|  
|`Properties`|可选 `String` 参数。<br /><br /> 以分号分隔的作为全局属性应用到子项目的属性名称/值对列表。 当你指定此参数时，它在功能上等效于在使用[MSBuild.exe](../msbuild/msbuild-command-line-reference.md)生成时设置具有 **/property**开关的属性。 例如：<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> 通过 `Properties` 参数将属性传递到项目时，即使已加载了项目文件，[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 也会创建项目的新实例。 创建项目的新实例后，[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 将其视为具有不同全局属性且可与项目的其他实例并行生成的不同项目。 例如，可同时生成发布配置和调试配置。|  
|`RebaseOutputs`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则生成项目中目标输出项的相对路径将其路径调整为相对于调用项目。 默认值为 `false`。|  
|`RemoveProperties`|可选 `String` 参数。<br /><br /> 指定要删除的全局属性的集。|  
|`RunEachTargetSeparately`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 任务一次一个地调用被传递到 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 的列表中调用一个目标，不会同时调用目标。 将此参数设置为 `true` 可确保即使先前调用目标失败，也可调用后续目标。 否则，生成错误将停止调用所有后续目标。 默认值为 `false`。|  
|`SkipNonexistentProjects`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则将跳过磁盘上不存在的项目文件。 否则，此类项目会引发错误。|  
|`StopOnFirstFailure`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，当其中一个项目生成失败时，则不会再生成其他项目。 目前在并行生成时（具有多个处理器）不支持此参数。|  
|`TargetAndPropertyListSeparators`|可选 `String[]` 参数。<br /><br /> 将目标和属性的列表指定为 `Project` 项元数据）。 进行处理前，分隔符为非转义的。 例如 %3B（转义的“;”）将被视为未转义的“;”。|  
|`TargetOutputs`|可选的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 只读输出参数。<br /><br /> 返回出自所有项目文件的生成目标的输出。 仅返回出自所指定目标的输出，不返回存在于目标所依赖的目标上的任何输出。<br /><br /> `TargetOutputs` 参数还包含以下元数据：<br /><br /> -   `MSBuildSourceProjectFile`：包含设置输出的目标的 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 项目文件。<br />-   `MSBuildSourceTargetName`：设置输出的目标。 **注意：** 如果要分别识别每个项目文件或目标中的输出，请为每个项目文件或目标分别运行 `MSBuild` 任务。 如果只运行一次 `MSBuild` 任务来生成所有的项目文件，则会将所有目标的输出收集到一个数组中。|  
|`Targets`|可选 `String` 参数。<br /><br /> 指定要在项目文件中生成的一个或多个目标。 使用分号分隔一系列目标名称。 如果未在 `MSBuild` 任务中指定任何目标，则会生成在项目文件中指定的默认目标。 **注意：** 目标必须发生在所有项目文件中。 如果它们不发生在所有文件中，则会出现生成错误。|  
|`ToolsVersion`|可选 `String` 参数。<br /><br /> 指定生成项目被传递到此任务时要使用的 `ToolsVersion`。<br /><br /> 使 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 任务能够生成一个项目，该项目以 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 的其他版本为目标，而不是项目中指定的版本。 有效值为 `2.0`、`3.0` 和 `3.5`。 默认值是 `3.5`。|  
|`UnloadProjectsOnCompletion`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则在操作完成后，将立即卸载项目。|  
|`UseResultsCache`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则将返回缓存的结果（如果存在）。 如果运行 MSBuild 任务，会将其结果缓存在某个范围内 (ProjectFileName, GlobalProperties)[TargetNames]<br /><br /> 作为生成项的列表|  
  
## <a name="remarks"></a>备注  
 除上面列出的参数外，此任务还从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，后者自身继承自 <xref:Microsoft.Build.Utilities.Task> 类。 有关这些其他参数及其说明的列表，请参阅 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
 与使用 [Exec 任务](../msbuild/exec-task.md) 启动 MSBuild.exe 不同，此任务使用相同的 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 过程来生成子项目。 可跳过的已生成目标的列表在父级版本和子级版本之间共享。 此外，此任务速度更快，因为没有创建新的 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 进程。  
  
 此任务不仅可处理项目文件，还可处理解决方案文件。  
  
 必须使用配置文件使 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 使项目在同一时间生成所需的任何配置成为可配置的状态，即使配置中包含远程基础结构（例如端口、协议、超时、重试等）也是如此。 如果可能，应能够在 `MSBuild` 任务上将配置项指定为任务参数。  
  
 从 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5 起，解决方案项目现在展示来自其生成的所有子项目的 TargetOutputs。  
  
## <a name="passing-properties-to-projects"></a>将属性传递给项目  
 在 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5 之前的 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 版本中，将不同的属性集传递到 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 项中列出的不同项目具有一定的挑战性。 如果使用 [Msbuild 任务](../msbuild/msbuild-task.md)的 Properties 属性，则其设置将应用到所有正在生成的项目，除非你批处理 [MSBuild 任务](../msbuild/msbuild-task.md) 并有条件地为项列表中的每个项目提供不同的属性。  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 但3.5 提供了两个新的保留元数据项，属性和 AdditionalProperties，为你提供了一种灵活的方式来为使用 [MSBuild 任务](../msbuild/msbuild-task.md)生成的不同项目传递不同的属性。  
  
> [!NOTE]
> 这些新的元数据项仅适用于在 [MSBuild 任务](../msbuild/msbuild-task.md)的 "项目" 特性中传递的项。  
  
## <a name="multi-processor-build-benefits"></a>多处理器生成的优点  
 在多处理器系统上并行生成项目时，则会体验到使用此新元数据的其中一个主要的好处。 使用元数据可以将所有项目合并为单个 [MSBuild 任务](../msbuild/msbuild-task.md) 调用，而无需执行任何批处理或条件 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 任务。 当只调用单个 [MSBuild 任务](../msbuild/msbuild-task.md)时，将并行生成项目属性中列出的所有项目。 但 (仅 `BuildInParallel=true` 在 [MSBuild 任务](../msbuild/msbuild-task.md)中存在该属性。有关详细信息，请参阅 [并行生成多个项目](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)。 ) 有关详细信息，请参阅。  
  
## <a name="properties-metadata"></a>属性元数据  
 常见的情况是，使用 [MSBuild 任务](../msbuild/msbuild-task.md)构建多个解决方案文件时，只使用不同的生成配置。 你可能希望使用调试配置生成解决方案 a1，使用发布配置生成解决方案 a2。 在 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0 中，此项目文件将如下所示：  
  
> [!NOTE]
> 在以下示例中，“...”表示其他解决方案文件。  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 不过，通过使用属性元数据，你可以简化此操作，以使用单个 [MSBuild 任务](../msbuild/msbuild-task.md)，如下所示：  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <Properties>Configuration=Debug</Properties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"/>  
    </Target>  
</Project>  
```  
  
 \- 或 -  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…"/>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Debug"/>  
    </Target>  
</Project>  
```  
  
## <a name="additionalproperties-metadata"></a>AdditionalProperties 元数据  
 请考虑以下方案：使用 [MSBuild 任务](../msbuild/msbuild-task.md)构建两个解决方案文件，这两个文件都使用 Release 配置，但使用 x86 体系结构，另一个使用 ia64 体系结构。 在 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0 中，需要创建 [MSBuild 任务](../msbuild/msbuild-task.md)的多个实例：一个用于使用 x86 体系结构的 "发布" 配置生成项目，另一个用于使用 ia64 体系结构的发布配置。 项目文件将如下所示：  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln…" Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  
  
 使用 AdditionalProperties 元数据，可以通过以下方法简化此操作，以使用单个 [MSBuild 任务](../msbuild/msbuild-task.md) ：  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <AdditionalProperties>Architecture=x86  
              </AdditionalProperties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <AdditionalProperties>Architecture=ia64  
              </AdditionalProperties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>示例  
 以下示例使用 `MSBuild` 任务来生成由 `ProjectReferences` 项集合指定的项目。 生成的目标输出存储在 `AssembliesBuiltByChildProjects` 项集合中。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ProjectReferences Include="*.*proj" />  
    </ItemGroup>  
  
    <Target Name="BuildOtherProjects">  
        <MSBuild  
            Projects="@(ProjectReferences)"  
            Targets="Build">  
            <Output  
                TaskParameter="TargetOutputs"  
                ItemName="AssembliesBuiltByChildProjects" />  
        </MSBuild>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>另请参阅  
 [操作](../msbuild/msbuild-tasks.md)   
 [任务引用](../msbuild/msbuild-task-reference.md)
