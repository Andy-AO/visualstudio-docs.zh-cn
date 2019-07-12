---
title: 使用依赖项关系图验证代码
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e21c3699d796d6037d3b8ca0e744e792b9810b6
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824542"
---
# <a name="validate-code-with-dependency-diagrams"></a>使用依赖项关系图验证代码

## <a name="why-use-dependency-diagrams"></a>为什么使用依赖项关系图？

为了确保代码与其设计不冲突，请使用验证代码在 Visual Studio 中的依赖项关系图。 这可帮助你：

- 依赖项关系图上查找你的代码中的依赖关系和依赖项之间的冲突。

- 查找建议的更改可能会影响的依赖项。

   例如，你可以编辑依赖项关系图以显示潜在的体系结构更改，然后验证代码以查看受影响的依赖项。

- 将代码重构或迁移到其他设计。

   查找在将代码移动到其他体系结构时需要工作的代码或依赖项。

**要求**

- Visual Studio

- 一个具有建模项目和依赖项关系图的解决方案。 此依赖项关系图必须链接到你想要验证的 C# 或 Visual Basic 项目中的项目。 请参阅[从代码创建依赖项关系图](../modeling/create-layer-diagrams-from-your-code.md)。

> [!NOTE]
> 不支持在 Visual Studio 中的.NET Core 项目的依赖项关系图。

若要查看哪些版本的 Visual Studio 支持此功能，请参阅[体系结构和建模工具的版本支持](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

你可以验证代码手动从 Visual Studio 中打开的依赖项关系图或从命令提示符。 您还可以验证代码自动运行本地生成或 Azure 管道构建系统时。 请参阅[第 9 频道视频：设计和验证体系结构使用依赖项关系图](http://go.microsoft.com/fwlink/?LinkID=252073)。

> [!IMPORTANT]
> 如果你想要运行使用 Team Foundation Server (TFS) 的层验证，还必须在生成服务器上安装相同版本的 Visual Studio。

## <a name="live-dependency-validation"></a>实时依赖项验证

在真实时间中进行依赖关系验证和错误将立即显示在**错误列表**。

* 对于 C# 和 Visual Basic 支持实时验证。

* 若要使用实时依赖项验证时，请启用完整解决方案分析，可从黄色条框中显示打开的选项设置**错误列表**。

  - 如果您不想要查看你的解决方案中的所有体系结构问题，您可以永久消除黄色条框。
  - 如果未启用完整解决方案分析，仅对正在编辑的文件进行分析。

* 升级项目以启用实时验证时, 显示转换的进度的对话框。

* 更新以进行实时依赖项验证项目，NuGet 包的版本都已升级的所有项目相同，并且正在使用的最高版本。

* 添加新的依赖项验证项目触发项目更新。

## <a name="see-if-an-item-supports-validation"></a>查看项是否支持验证

你可以将层链接到网站、 Office 文档、 纯文本文件和项目中的多个应用之间共享文件，但验证过程不包含它们。 如果引用的项目或程序集链接到单独的层，而且这些层之间没有依赖关系出现，则将不会出现验证错误。 除非代码使用此类引用，否则这些引用不被视为依赖项。

1. 在依赖项关系图中，选择一个或多个层，用鼠标右键单击你的选择，然后单击**查看链接**。

2. 在中**层资源管理器**，看看**支持验证**列。 如果该值为 false，则项不支持验证。

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>包括其他 .NET 程序集和项目以进行验证

将项拖到依赖项关系图中，对相应的.NET 程序集或项目的引用将自动添加到**层引用**建模项目中的文件夹。 此文件夹包含对验证过程中分析的程序集和项目的引用。 可以包含其他.NET 程序集和项目以进行验证，而无需手动将其拖动到依赖项关系图。

1. 在中**解决方案资源管理器**，右键单击建模项目或**层引用**文件夹，，然后单击**添加引用**。

2. 在中**添加引用**对话框中，选择程序集或项目，然后依次**确定**。

## <a name="validate-code-manually"></a>手动验证代码

如果你有链接到解决方案项打开的依赖项关系图，则可以运行**验证**从关系图的快捷方式命令。 此外可以使用命令提示符处运行**msbuild**命令 **/p:ValidateArchitecture**自定义属性设置为**True**。 例如，在对代码进行更改时，请定期执行层验证以便能够提前捕获依赖项冲突。

### <a name="validate-code-from-an-open-dependency-diagram"></a>从打开的依赖项关系图验证代码

1. 右键单击关系图图面，然后依次**验证体系结构**。

    > [!NOTE]
    > 默认情况下**生成操作**上的依赖项关系图 (.layerdiagram) 文件的属性设置为**验证**，以便在验证过程中包括关系图。

     **错误列表**窗口报告出现的任何错误。 有关验证错误的详细信息，请参阅[层验证问题疑难解答](#troubleshoot-layer-validation-issues)。

2. 若要查看每个错误的源，请双击中的错误**错误列表**窗口。

    > [!NOTE]
    > Visual Studio 可能会显示代码图，而不是错误的源。 代码不由依赖项关系图中，指定程序集上具有依赖项或代码缺少指定的依赖项关系图的依赖项时，将发生这种情况。 检查代码映射或代码，以确定此依赖关系是否应该存在。 有关代码图的详细信息，请参阅[映射解决方案之间的依赖项](../modeling/map-dependencies-across-your-solutions.md)。

3. 若要管理错误，请参阅[纠正层验证错误](#resolve-layer-validation-errors)。

### <a name="validate-code-at-the-command-prompt"></a>命令提示符处验证代码

1. 打开 Visual Studio 命令提示符。

2. 选择以下选项之一：

   - 若要对照解决方案中的特定建模项目验证代码，请使用下面的自定义属性运行 MSBuild。

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - 或 -

       浏览到包含建模项目 (.modelproj) 的文件夹文件和依赖项关系图，然后使用下面的自定义属性运行 MSBuild:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - 若要对照解决方案中的所有建模项目验证代码，请使用下面的自定义属性运行 MSBuild:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - 或 -

       浏览到解决方案文件夹，其中必须包含一个包含依赖项关系图的建模项目，然后使用下面的自定义属性中运行 MSBuild:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     将列出发生的任何错误。 有关 MSBuild 的详细信息，请参阅[MSBuild](../msbuild/msbuild.md)并[MSBuild 任务](../msbuild/msbuild-task.md)。

   有关验证错误的详细信息，请参阅[层验证问题疑难解答](#troubleshoot-layer-validation-issues)。

### <a name="manage-validation-errors"></a>管理验证错误

在开发过程中，你可能需要在验证期间禁止显示报告的某些冲突。 例如，你可能希望禁止显示你已解决或与特定情形不相关的错误。 禁止显示错误时，最好能够登录 Team Foundation 工作项。

> [!WARNING]
> 必须已连接到 TFS 源代码管理 (SCC) 才可创建或链接到工作项。 如果尝试打开到其他 TFS SCC 的连接，则 Visual Studio 会自动关闭当前解决方案。 请先确保已连接到相应的 SCC，然后再尝试创建或链接到工作项。 在更高版本的 Visual Studio 中，如果未连接到 SCC，则菜单命令不可用。

#### <a name="create-a-work-item-for-a-validation-error"></a>创建工作项的验证错误

- 在中**错误列表**窗口中，右键单击错误，指向**创建工作项**，然后单击你想要创建的工作项的类型。

使用这些任务来管理中的验证错误**错误列表**窗口：

|**若要**|**请执行以下步骤**|
|-|-|
|禁止在验证过程中显示选定的错误|右键单击一个或多个所选的错误，指向**管理验证错误**，然后单击**禁止显示错误**。<br /><br /> 禁止显示的错误在显示时均带有删除线格式。 在你下次运行验证时，这些错误将不会显示。<br /><br /> 相应的依赖项关系图文件的.suppressions 文件中跟踪的禁止显示的错误。|
|停止禁止显示选定的错误|右键单击所选的禁止显示的错误，指向**管理验证错误**，然后单击**停止禁止显示错误**。<br /><br /> 在你下次运行验证时，这些所选的禁止显示的错误将会显示。|
|还原中的所有禁止显示的错误**错误列表**窗口|中的任意位置右击**错误列表**窗口中，依次指向**管理验证错误**，然后单击**显示所有禁止显示的错误**。|
|隐藏所有禁止显示的错误**错误列表**窗口|中的任意位置右击**错误列表**窗口中，依次指向**管理验证错误**，然后单击**隐藏所有禁止显示的错误**。|

## <a name="validate-code-automatically"></a>自动验证代码

每次运行本地生成时，都可以执行层验证。 如果你的团队使用 Azure DevOps，则可以执行与封闭签入，这可以通过创建自定义 MSBuild 任务，并使用生成报告来收集验证错误指定的层验证。 若要创建封闭的签入生成，请参阅[TFVC 封闭签入](/azure/devops/pipelines/build/triggers#gated)。

### <a name="to-validate-code-automatically-during-a-local-build"></a>在本地生成期间自动验证代码

使用文本编辑器打开建模项目 (.modelproj) 文件，然后包括以下属性：

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- 或 -

1. 在中**解决方案资源管理器**，右键单击包含依赖项关系图或关系图的建模项目，然后单击**属性**。

2. 在中**属性**窗口中，将建模项目**验证体系结构**属性设置为**True**。

    这将在验证过程中包括建模项目。

3. 在中**解决方案资源管理器**，单击你想要用于验证的依赖项关系图 (.layerdiagram) 文件。

4. 在中**属性**窗口中，请确保关系图的**生成操作**属性设置为**Validate**。

    这包括在验证过程中的依赖项关系图。

若要管理错误列表窗口中的错误，请参阅[纠正层验证错误](#resolve-layer-validation-errors)。

## <a name="troubleshoot-layer-validation-issues"></a>层验证问题疑难解答

下表描述了层验证问题及其解决方法。 这些问题不同于代码与设计发生冲突而导致出现的错误。 有关这些错误的详细信息，请参阅[层验证问题疑难解答](#troubleshoot-layer-validation-issues)。

|**问题**|**可能的原因**|**解决方法**|
|-|-|-|
|验证错误不按预期发生。|从解决方案资源管理器中的其他依赖项关系图复制的和相同的建模项目中存在的依赖项关系图时，验证不起作用。 在这种方式中复制的依赖项关系图包含与原始的依赖项关系图相同的引用。|将新的依赖项关系图添加到建模项目。<br /><br /> 源依赖项关系图中的元素复制到新关系图中。|

## <a name="resolve-layer-validation-errors"></a>纠正层验证错误

当验证对依赖项关系图的代码时，当代码与设计发生冲突时，会发生验证错误。 例如，以下情况可能导致发生验证错误：

- 将项目指派给了错误的层。 在这种情况下，请移动项目。

- 项目（例如类）以与你的体系结构相冲突的方式使用了其他类。 在这种情况下，请重构代码以移除依赖关系。

若要解决这些错误，请更新代码，直至验证过程中不出现其他错误为止。 可以反复执行此任务。

以下各节描述这些错误中使用的语法，解释了这些错误的含义，并提供了纠正或管理这些错误的方法。

|**语法**|**说明**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN*是与依赖项关系图上关联的项目。<br /><br /> *ArtifactTypeN*是一种*ArtifactN*，如**类**或**方法**，例如：<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|命名空间的名称。|
|*LayerNameN*|依赖项关系图上的名称。|
|*DependencyType*|类型之间的依赖关系*Artifact1*并*Artifact2*。 例如， *Artifact1*已**调用**与关系*Artifact2*。|

| **错误语法** | **错误说明** |
|-|-|
| DV0001:**无效的依赖关系** | 代码元素 （命名空间、 类型和成员） 映射到层引用代码元素映射到另一层，但这些依赖关系验证关系图包含此层中的各层之间没有任何依赖项箭头时，会报告此问题。 这是依赖关系约束冲突。 |
| DV1001:**无效的命名空间名称** | 此问题将报告与层"允许 Namespace 名称"属性未包含在其中定义此代码元素的命名空间关联的代码元素上。 这是一个命名的约束冲突。 请注意，"允许 Namespace 名称"的语法是以分号列表的命名空间中的代码与关联的元素是层允许进行定义。 |
| DV1002:**不可引用命名空间的依赖关系** | 此问题将报告上一个代码元素与层关联和引用层"不可引用 Namespace"属性中定义的命名空间中定义的另一个代码元素。 这是一个命名的约束冲突。 请注意，"不可引用命名空间"属性被定义为不应与此层相关联的代码元素中引用的命名空间的以分号分隔列表。 |
| DV1003:**禁用的命名空间名称** | 与"不允许使用 Namespace 名称"属性包含在其中定义此代码元素的命名空间的层关联的代码元素上报告此问题。 这是一个命名的约束冲突。 请注意，"不允许命名空间名称"属性被定义为命名空间中的代码不应定义与此层相关联的元素的以分号分隔列表。 |
| DV3001:**缺少链接** | 层 '*LayerName*链接到*项目*找不到其中。 是否缺少程序集引用? |
| DV9001:**体系结构分析找到的内部错误** | 结果可能不完整。 有关详细信息，请参阅详细的生成事件日志或输出窗口。 |

## <a name="see-also"></a>请参阅

- [Visual Studio 中的实时依赖项验证](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [在开发过程中验证系统](../modeling/validate-your-system-during-development.md)
- [视频：验证你在真实时间中的体系结构依赖关系](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
