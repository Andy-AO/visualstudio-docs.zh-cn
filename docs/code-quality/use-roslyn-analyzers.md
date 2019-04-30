---
title: 分析器规则严重性和禁止显示
ms.date: 03/26/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 56637ee7826b944d739e170faf22ae354abd8adc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821280"
---
# <a name="use-roslyn-analyzers"></a>使用 Roslyn 分析器

.NET 编译器平台 ("Roslyn") 分析程序规则，或*诊断*，键入分析 C# 或 Visual Basic 代码。 每个诊断已为你的项目时可以覆盖默认严重性和禁止显示状态。 本文介绍如何设置规则严重性，使用规则集，并禁止显示冲突。

## <a name="analyzers-in-solution-explorer"></a>在解决方案资源管理器中的分析器

可以执行自定义分析器诊断从大量**解决方案资源管理器**。 如果您[安装分析器](../code-quality/install-roslyn-analyzers.md)NuGet 包，作为**分析器**下会显示节点**引用**或**依赖项**中的节点**解决方案资源管理器**。 如果展开**分析器**，，然后展开其中一个分析器程序集，请参阅在程序集中的所有诊断。

![在解决方案资源管理器中的分析器节点](media/analyzers-expanded-in-solution-explorer.png)

您可以查看诊断，包括其说明和默认严重性中的属性**属性**窗口。 若要查看属性，请右键单击该规则并选择**属性**，或选择该规则，然后按**Alt**+**Enter**。

![在属性窗口中的诊断属性](media/analyzer-diagnostic-properties.png)

若要查看联机文档的诊断，诊断右键单击并选择**查看帮助**。

中的每个诊断旁的图标**解决方案资源管理器**对应于所示的规则集编辑器中打开它时的图标：

- 在圆圈中的"i"指示[严重性](#rule-severity)的**信息**
- "！"在一个三角形指示[严重性](#rule-severity)的**警告**
- 在圆圈中的"x"指示[严重性](#rule-severity)的**错误**
- 圆形浅色背景上的"i"指示[严重性](#rule-severity)的**隐藏**
- 在圆圈中的向下箭头指示取消诊断

![在解决方案资源管理器中的诊断图标](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>规则集

一个[规则集](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)是存储为单个诊断的严重性和禁止显示状态的 XML 文件。

> [!NOTE]
> 规则集可以包括 （二进制） 的静态代码分析和 Roslyn 分析器中的规则。

若要编辑的规则集编辑器中设置活动规则，请右键单击**引用** > **分析器**中的节点**解决方案资源管理器**，然后选择**打开活动规则集**。 如果是第一次你正在编辑的规则集，Visual Studio 创建设置文件的默认规则的副本，其*\<项目名称 >.ruleset*，并将其添加到你的项目。 此自定义规则集也将成为活动的规则设置为你的项目。

若要更改活动规则集的项目，请导航到**代码分析**项目的属性选项卡。 选择规则集从下的列表**运行此规则集**。 若要打开规则集，请选择**打开**。

> [!NOTE]
> .NET core 和.NET Standard 项目的规则设置中不支持的菜单命令**解决方案资源管理器**，例如**打开活动规则集**。 若要指定非默认规则设置对于.NET Core 或.NET Standard 项目中，手动[添加**CodeAnalysisRuleSet**属性设置为项目文件](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project)。 可以配置规则在 Visual Studio 中设置规则集编辑器 UI 中的规则。

## <a name="rule-severity"></a>规则严重性

你可以配置在分析程序规则的严重性或*诊断*，如果您[安装分析器](../code-quality/install-roslyn-analyzers.md)作为 NuGet 包。 下表显示了用于诊断的严重性选项：

|严重性|生成时的行为|编辑器行为|
|-|-|-|
|Error|会显示冲突了作为*错误*中**错误列表**和在命令行生成输出，并会导致生成失败。|有问题的代码带有红色波浪线，并通过在滚动条小红色框标记为带有下划线。|
|警告|会显示冲突了作为*警告*中**错误列表**和在命令行生成输出，但不是会导致生成失败。|有问题的代码与绿色波浪线，并通过滚动条中的小绿色框标记为带有下划线。|
|T:System.Diagnostics.Switch|会显示冲突了作为*消息*中**错误列表**，根本不在命令行生成输出。|有问题的代码带有下划线用波浪线，并通过滚动条中的小灰色框标记为灰色。|
|Hidden|非-对用户可见。|非-对用户可见。 诊断报告到 IDE 诊断引擎，但是。|
|None|完全禁止显示。|完全禁止显示。|

此外，你可以"重置"规则的严重性设置为**默认**。 每个诊断具有所示的默认严重性**属性**窗口。

下面的屏幕截图显示了在代码编辑器中，具有三个不同的严重级别的三个不同的诊断冲突。 请注意，波浪线，以及在右侧的滚动条中的小框的颜色。

![在代码编辑器中的错误、 警告和信息冲突](media/diagnostics-severity-colors.png)

以下屏幕截图显示了相同的三个冲突，出现在**错误列表**:

![错误列表中的错误、 警告和信息冲突](media/diagnostics-severities-in-error-list.png)

您可以更改的规则的严重性**解决方案资源管理器**，或在 *\<projectname >.ruleset*后更改的重要程度中的规则添加到解决方案的文件**解决方案资源管理器**。

![在解决方案资源管理器中的规则集文件](media/ruleset-in-solution-explorer.png)

### <a name="set-rule-severity-from-solution-explorer"></a>从解决方案资源管理器中设置规则严重性

1. 在**解决方案资源管理器**，展开**引用** > **分析器**(**依赖关系** >  **分析器**有关.NET Core 项目)。

1. 展开包含你想要设置的严重程度的规则的程序集。

1. 右键单击规则并选择**设置规则集严重性**。 在弹出菜单中，选择一个严重性选项。

   规则严重性被保存在活动规则集文件中。

### <a name="set-rule-severity-in-the-rule-set-file"></a>在规则集文件中设置规则严重性

1. 打开[规则集](analyzer-rule-sets.md)中双击文件**解决方案资源管理器**，选择**打开活动规则集**上的右键单击菜单**分析器**节点，或选择**开放**上**代码分析**项目属性页。

1. 通过展开其包含程序集，浏览到该规则。

1. 在中**操作**列中，选择值以打开下拉列表，并从列表中选择所需的严重性。

   ![规则集文件在编辑器中打开](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>禁止显示冲突

有多种方法来禁止显示规则冲突：

- 从**分析**菜单

   选择**分析** > **运行代码分析并取消未解决的问题**要禁止显示所有当前的冲突的菜单栏上。 这有时称为"基线"。

- 从**解决方案资源管理器**

   若要禁止显示中的违反**解决方案资源管理器**，将该规则的严重性设置为**None**。

- 从**规则集编辑器**

   若要禁止显示从规则集编辑器的冲突，请取消选中其名称旁边的框，或设置**操作**到**None**。

- 从**代码编辑器**

   若要禁止显示代码编辑器中的冲突，请将光标放置在一行代码冲突并按**Ctrl**+**。** 若要打开**快速操作**菜单。 选择**禁止显示 CAXXXX** > **源/禁止显示文件**。

   ![禁止显示诊断从快速操作菜单](media/suppress-diagnostic-from-editor.png)

- 从**错误列表**

   您可以禁止显示来自一个或多个诊断**错误列表**的选择的想要禁止显示，并单击右键并选择**禁止** > **中 Source/In禁止显示文件**。

   - 如果您禁止显示**在源**，则**预览更改**对话框将打开并显示的预览C# [#pragma 警告](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning)或 Visual Basic [#Disable警告](/dotnet/visual-basic/language-reference/directives/directives)指令添加到源代码。

      ![在代码文件中添加 #pragma 警告的预览](media/pragma-warning-preview.png)

   - 如果选择**在禁止显示文件**，则**预览更改**对话框将打开并显示的预览<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>添加到全局禁止显示文件的属性。

      ![SuppressMessage 特性添加到禁止显示文件的预览](media/preview-changes-in-suppression-file.png)

   在中**预览更改**对话框中，选择**应用**。

   > [!NOTE]
   > 如果没有看到**禁止**中的菜单选项**解决方案资源管理器**，冲突可能来自生成和不实时分析。 **错误列表**显示诊断或从这两个冲突实时代码分析和生成的规则。 由于生成诊断可能是陈旧，例如，如果你已编辑代码来解决冲突，但尚未重新生成，无法禁止显示来自这些诊断**错误列表**。 来自实时分析或智能感知，诊断始终是当前源代码的最新，并可从抑制**错误列表**。 若要排除*构建*从你的选择，诊断切换**错误列表**源筛选器从**生成 + IntelliSense**到**仅 Intellisense**. 然后，选择你想要取消，并在继续操作，因为前面所述的诊断。
   >
   > ![在 Visual Studio 中的错误列表源筛选器](media/error-list-filter.png)

## <a name="command-line-usage"></a>命令行使用情况

生成你的项目在命令行时，规则冲突显示在生成输出中，如果满足以下条件：

- 分析器以 Nuget 包的形式而不是作为 VSIX 扩展安装。

- 在项目的代码中违反一个或多个规则。

- [严重性](#rule-severity)违反规则的设置为**警告**，在这种情况下冲突不会导致生成失败，或**错误**，违反这种情况下导致生成失败。

生成输出详细级别不会影响是否显示规则冲突。 即使**安静**详细级别，在生成输出中会显示的规则冲突。

> [!TIP]
> 如果您习惯于在命令行中，通过运行静态代码分析*FxCopCmd.exe*或通过使用 msbuild **RunCodeAnalysis**标志，下面介绍了如何使用 Roslyn 分析器执行该操作。

若要生成使用 msbuild 的项目时，请查看在命令行分析器冲突，请运行如下命令：

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

下图显示了构建包含分析器规则冲突的项目的命令行生成输出：

![带规则冲突的 MSBuild 输出](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>相关项目

在.NET Core 项目中，如果添加对具有 NuGet 分析器的项目的引用这些分析器将自动添加到依赖项目太。 若要禁用此行为，例如，如果依赖项目是单元测试项目，将标记为在专用的 NuGet 包 *.csproj*或 *.vbproj*文件引用的项目，通过设置**PrivateAssets**属性：

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>请参阅

- [在 Visual Studio 中的 Roslyn 分析器的概述](../code-quality/roslyn-analyzers-overview.md)
- [提交 Roslyn 分析器错误](https://github.com/dotnet/roslyn-analyzers/issues)
- [使用规则集](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [禁止显示代码分析警告](../code-quality/in-source-suppression-overview.md)