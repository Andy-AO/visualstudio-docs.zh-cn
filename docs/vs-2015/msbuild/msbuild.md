---
title: MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
caps.latest.revision: 62
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4fb99a7f7fcd7c91003bc7d74cf0ef6639cf773
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698042"
---
# <a name="msbuild"></a>MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] 是一个用于生成应用程序的平台。 此引擎（也称为 MSBuild）为项目文件提供了一个 XML 架构，用于控制生成平台处理和生成软件的方式。 Visual Studio 会使用 MSBuild，但它不依赖于 Visual Studio。 通过在你的项目或解决方案文件中调用 msbuild.exe，你可以在未安装 Visual Studio 的环境中安排和生成产品。  
  
 Visual Studio 使用 MSBuild 来加载和生成托管项目。 Visual Studio 中的项目文件（.csproj、.vbproj、vcxproj 等）包含 MSBuild XML 代码，当你使用 IDE 来生成项目时，此代码就会运行。 Visual Studio 项目会导入所有必要的设置和生成过程来执行典型的开发工作，但你可以从 Visual Studio 内或通过使用 XML 编辑器对其进行扩展或修改。  
  
 有关适用于 C++ 的 MSBuild 的信息，请参阅 [MSBuild (Visual C++)](https://msdn.microsoft.com/library/7a1be7ff-0312-4669-adf2-5f5bf507d560)。  
  
 下面的示例介绍了什么情况下可使用 MSBuild 命令行而不是 Visual Studio IDE 来运行生成。  
  
- 未安装 Visual Studio。  
  
- 你想要使用 64 位版本的 MSBuild。 通常情况下不必使用此版本的 MSBuild，但它可以让 MSBuild 访问更多内存。  
  
- 你想要在多个进程中运行同一生成。 不过，对于 C++ 和 C# 中的项目，你可以使用 IDE 实现相同的结果。  
  
- 你想要修改生成系统。 例如，你可能想要实现以下操作：  
  
  - 在文件到达编译器之前先进行预处理。  
  
  - 将生成输出复制到其他位置。  
  
  - 从生成输出创建压缩文件。  
  
  - 执行后处理步骤。 例如，你可能希望使用其他版本来标记程序集。  
  
  你可以在 Visual Studio IDE 中编写代码，但使用 MSBuild 来运行生成。 或者，你也可以在开发计算机的 IDE 中生成代码，但使用 MSBuild 命令行生成从多个开发人员集成的代码。  
  
> [!NOTE]
> 你可以使用 Team Foundation Build 自动编译、测试和部署你的应用程序。 你的生成系统会在开发人员签入代码（例如，作为持续集成策略的一部分）时或按照计划（例如，夜间版本验证测试生成）自动运行生成。 Team Foundation Build 使用 MSBuild 来编译你的代码。 有关详细信息，请参阅[生成应用程序](https://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)。  
  
 本主题概述了 MSBuild。 有关介绍性教程，请参阅[演练：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)。  
  
 **在本主题中**  
  
- [在命令提示符处使用 MSBuild](#BKMK_CommandPrompt)  
  
- [项目文件](#BKMK_ProjectFile)  
  
    - [属性](#BKMK_Properties)  
  
    - [项](#BKMK_Items)  
  
    - [任务](#BKMK_Tasks)  
  
    - [目标](#BKMK_Targets)  
  
- [生成日志](#BKMK_BuildLogs)  
  
- [在 Visual Studio 中使用 MSBuild](#BKMK_VisualStudio)  
  
- [多定向](#BKMK_Multitargeting)  
  
## <a name="BKMK_CommandPrompt"></a>在命令提示符处使用 MSBuild  
 若要在命令提示符处运行 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]，请将项目文件随相应的命令行选项一起传递到 MSBuild.exe。 命令行选项允许你设置属性、执行特定的目标，以及设置可控制生成过程的其他选项。 例如，使用以下命令行语法生成文件 `MyProj.proj`，并将 `Configuration` 属性设置为 `Debug`。  
  
```  
MSBuild.exe MyProj.proj /property:Configuration=Debug  
```  
  
 有关 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 命令行选项的详细信息，请参阅[命令行参考](../msbuild/msbuild-command-line-reference.md)。  
  
> [!IMPORTANT]
> 在下载项目之前，请确定代码的可信度。  
  
## <a name="BKMK_ProjectFile"></a>项目文件  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 使用基于 XML 的项目文件格式，既简单又可扩展。 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 项目文件格式允许开发者描述要生成的项，以及如何针对不同的操作系统和配置生成这些项。 另外，这种项目文件格式还允许开发人员创作可重用的生成规则，这些规则可以包含到不同的文件中，以便可以在产品内的不同项目之间一致地执行生成。  
  
 以下各节介绍了 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 项目文件格式的一些基本元素。 有关如何创建基本项目文件的教程，请参见[演练：从头开始创建 MSBuild 项目文件](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)。  
  
### <a name="BKMK_Properties"></a>属性  
 属性表示可用于配置生成的键/值对。 属性的声明方式是：创建一个与属性同名的元素，将其指定为 [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) 元素的子元素。 例如，下面的代码将创建一个名为 `BuildDir` 的属性，其值为 `Build`。  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 通过在元素中放置一个 `Condition` 属性，你可以有条件地定义一个属性。 除非条件的计算结果为 `true`，否则会忽略条件元素的内容。 在下面的示例中，将定义 `Configuration` 元素（如果尚未定义）。  
  
```  
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 在整个项目文件中，可以使用语法 $ (*PropertyName*) 来引用各个属性。 例如，可以使用 `$(BuildDir)` 和 `$(Configuration)` 来引用前面示例中的属性。  
  
 有关属性的详细信息，请参阅 [MSBuild 属性](msbuild-properties1.md)。  
  
### <a name="BKMK_Items"></a>项  
 项是生成系统的输入，通常表示文件。 将根据用户定义的项名称，将项编组到各种项类型中。 这些项类型可以用作任务的参数，任务使用各个项来执行生成过程的步骤。  
  
 项目文件中项的声明方法是：通过创建一个与项类型同名的元素，并将其指定为 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 元素的子元素。 例如，下面的代码将创建一个名为 `Compile` 的项类型，其中包括两个文件。  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 在整个项目文件中，可以使用语法 @(*ItemType*) 来引用项类型。 例如，可以使用 `@(Compile)` 引用示例中的项类型。  
  
 在 MSBuild 中，元素和特性名称区分大小写。 但是，属性、项和元数据名称不区分大小写。 下面的示例创建了项类型 `Compile`、`comPile` 或任何其他大小写变体，并为其指定了值“one.cs;two.cs”。  
  
```  
<ItemGroup>  
  <Compile Include="one.cs" />  
  <comPile Include="two.cs" />  
</ItemGroup>  
```  
  
 可以使用通配符声明项，并且对于更高级的生成方案，项可以包含其他元数据。 有关项的详细信息，请参阅[项](../msbuild/msbuild-items.md)。  
  
### <a name="BKMK_Tasks"></a>任务  
 任务是 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 项目用于执行生成操作的可执行代码单元。 例如，任务可能编译输入文件或运行外部工具。 任务可以重用，并且可由不同项目中的不同开发人员共享。  
  
 任务的执行逻辑在托管代码中编写，并使用 [UsingTask](../msbuild/usingtask-element-msbuild.md) 元素映射到 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]。 你可以通过创作一个实现 <xref:Microsoft.Build.Framework.ITask> 接口的托管类型来编写自己的任务。 有关如何编写任务的详细信息，请参阅[任务写入](../msbuild/task-writing.md)。  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 包含一些可按需进行修改的常见任务。  例如，用于复制文件的[复制](../msbuild/copy-task.md)、用于创建目录的 [MakeDir](../msbuild/makedir-task.md) 以及用于编译 Visual C# 源代码文件的 [Csc](../msbuild/csc-task.md)。 有关可用任务的列表以及用法信息，请参阅 [任务参考](../msbuild/msbuild-task-reference.md)。  
  
 通过创建一个与任务同名的元素，并将其指定为 [Target](../msbuild/target-element-msbuild.md) 元素的子元素，以在 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 项目文件中执行此任务。 任务通常接受参数，参数将作为元素的特性进行传递。 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 的属性和项都可用作参数。 例如，以下代码将调用 [MakeDir](../msbuild/makedir-task.md) 任务，并将前面示例中声明的 `BuildDir` 属性的值传递到该任务。  
  
```  
<Target Name="MakeBuildDirectory">  
    <MakeDir  Directories="$(BuildDir)" />  
</Target>  
```  
  
 有关任务的详细信息，请参阅[任务](../msbuild/msbuild-tasks.md)。  
  
### <a name="BKMK_Targets"></a>目标  
 目标按特定的顺序将任务组合到一起，并将项目文件的各个部分公开为生成过程的入口点。 目标通常分组到各个逻辑部分中，以便提高可读性并实现扩展。 通过将生成步骤拆分为目标，你可以从其他目标中调用生成过程的一个部分，而不必将那部分代码复制到每个目标中。 例如，如果生成过程的多个入口点需要生成引用，你可以创建一个生成引用的目标，然后从所要求的每个入口点运行此目标。  
  
 目标是使用 [Target](../msbuild/target-element-msbuild.md) 元素在项目文件中声明的。 例如，以下代码将创建一个名为 `Compile` 的目标，该目标随后将调用具有前面示例中声明的项列表的 [Csc](../msbuild/csc-task.md) 任务。  
  
```  
<Target Name="Compile">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 在更高级的方案中，目标可用于描述彼此之间的关系并执行依赖性分析，这样，如果目标是最新的，则可以跳过生成过程的整个部分。 有关目标的更多信息，请参阅[目标](../msbuild/msbuild-targets.md)。  
  
## <a name="BKMK_BuildLogs"></a>生成日志  
 你可以将生成错误、警告和消息记录到控制台或其他输出设备。 有关详细信息，请参阅[获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)和 [MSBuild 中的日志记录](../msbuild/logging-in-msbuild.md)。  
  
## <a name="BKMK_VisualStudio"></a>在 Visual Studio 中使用 MSBuild  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 使用 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 项目文件格式来存储有关托管项目的生成信息。 通过使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 接口添加或更改的项目设置将反映在为每个项目生成的 .*proj 文件中。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 使用一个已承载的 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 实例来生成托管项目。 这意味着可以在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中或在命令提示符处生成托管项目（即使未安装 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]），并且结果将完全相同。  
  
 有关如何在 Visual Studio 中使用 MSBuild 的教程，请参阅[演练：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)。  
  
## <a name="BKMK_Multitargeting"></a>多定向  
 通过 Visual Studio，你可以将应用程序编译为在若干 .NET Framework 版本的任意一个上运行。 例如，可以将同一个应用程序编译为既能在 32 位平台的 .NET Framework 2.0 上运行，也能在 64 位平台的 .NET Framework 4.5 上运行。 这种使用多个框架作为编译目标的能力称为“多目标功能”。  
  
 以下是多目标功能的一些优点：  
  
- 可以开发以多个 .NET Framework 早期版本（例如，版本 2.0、3.0 和 3.5）为目标的应用程序。  
  
- 你可以将 .NET Framework 之外的框架作为目标，例如 Silverlight。  
  
- 可以一个*框架配置文件*为目标，该文件是目标框架的预定义子集。  
  
- 如果已发布 .NET Framework 当前版本的 Service Pack，则可以将其作为目标。  
  
- 多目标功能可以保证应用程序仅使用目标框架和平台中的可用功能。  
  
  有关详细信息，请参阅[多定向](../msbuild/msbuild-multitargeting-overview.md)。  
  
## <a name="related-topics"></a>相关主题  
  
|Title|描述|  
|-----------|-----------------|  
|[演练：从头创建 MSBuild 项目文件](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|演示如何只使用文本编辑器以增量方式创建基本项目文件。|  
|[演练：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)|介绍 MSBuild 的构建基块，并演示如何在不关闭 Visual Studio IDE 的情况下编写、操作和调试 MSBuild 项目。|  
|[MSBuild 概念](../msbuild/msbuild-concepts.md)|演示 MSBuild 的四个生成块：属性、项、目标和任务。|  
|[项](../msbuild/msbuild-items.md)|介绍 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 文件格式背后的常规概念，以及所有这些概念之间的关系。|  
|[MSBuild 属性](msbuild-properties1.md)|介绍属性和属性集合。 属性是可用于配置生成的键/值对。|  
|[目标](../msbuild/msbuild-targets.md)|介绍如何按特定的顺序将任务组合到一起，并允许从命令行调用生成过程的各个部分。|  
|[任务](../msbuild/msbuild-tasks.md)|演示如何创建 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 可用于执行原子生成操作的可执行代码单元。|  
|[条件](../msbuild/msbuild-conditions.md)|论述如何在 MSBuild 元素中使用 `Condition` 特性。|  
|[高级概念](../msbuild/msbuild-advanced-concepts.md)|演示批处理、执行转换、多目标和其他高级技术。|  
|[MSBuild 中的日志记录](../msbuild/logging-in-msbuild.md)|介绍如何记录生成事件、消息和错误。|  
|[其他资源](../msbuild/additional-msbuild-resources.md)|列出社区和支持资源，用于了解有关 MSBuild 的更多信息。|  
  
## <a name="reference"></a>参考  
 [MSBuild 参考](../msbuild/msbuild-reference.md)  
 链接到包含参考信息的主题。  
  
 词汇表  
 定义常见 MSBuild 术语。
