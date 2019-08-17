---
title: 分析器规则集
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c0be66559802188503c3b8f8c1c2cf2955dbd8a
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547951"
---
# <a name="rule-sets-for-analyzer-packages"></a>分析器包规则集

某些 NuGet 分析器包附带了预定义规则集。 例如, [CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet 分析器包附带的规则集 (从版本2.6.2 开始) 根据规则的类别 (如安全性、命名或性能) 启用或禁用规则。 使用规则集可以轻松地快速查看与特定规则类别相关的规则冲突。

如果要从旧的 "FxCop" 分析迁移到基于 .NET Compiler Platform 的代码分析, 则这些规则集使你可以继续使用以前使用过的相同规则配置。

## <a name="use-analyzer-package-rule-sets"></a>使用分析器包规则集

[安装 NuGet 分析器包](install-roslyn-analyzers.md)后, 请在其 "规则集" 目录中找到预定义的规则集。 例如, 如果你`Microsoft.CodeAnalysis.FxCopAnalyzers`引用了分析器包, 则可以在% USERPROFILE% *\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<版本中找到其规则集目录\rulesets\>* 。 在此处复制一个或多个规则集, 并将其粘贴到包含你的 Visual Studio 项目或直接**解决方案资源管理器**的目录中。

你还可以[自定义预定义的规则集](how-to-create-a-custom-rule-set.md), 并将其设置为首选项。 例如, 你可以更改一个或多个规则的严重性, 使冲突在**错误列表**中显示为错误或警告。

## <a name="set-the-active-rule-set"></a>设置活动规则集

设置活动规则集的过程稍有不同, 具体取决于你是否有 .NET Core/.net Standard 项目或 .NET Framework 项目。

### <a name="net-core"></a>.NET Core

若要将规则设置为在 .NET Core 或 .NET Standard 项目中进行分析, 请手动将**CodeAnalysisRuleSet**属性添加到项目文件。 例如, 以下代码片段设置`HelloWorld.ruleset`为活动规则集。

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

若要将规则设置为 .NET Framework 项目中的 "分析", 请在**解决方案资源管理器**中右键单击该项目, 然后选择 "**属性**"。 在项目属性页中, 选择 "**代码分析**" 选项卡。在 "**运行此规则集**" 下, 选择 "**浏览**", 然后选择已复制到项目目录的所需规则集。 现在, 你只会看到在所选规则集中启用的那些规则的规则冲突。

## <a name="available-rule-sets"></a>可用规则集

预定义的分析器规则集包括三个规则集, 这些规则会影响&mdash;包中的所有规则, 其中所有规则都允许所有规则, 一个用于禁用所有规则, 另一个用于接受每个规则的默认严重性和启用设置:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

此外, 包中的每个规则类别都有两个规则集, 如性能或安全性。 一个规则集启用类别的所有规则, 一个规则集遵循类别中每个规则的默认严重性和启用设置。

[CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet 分析器包包含以下类别的规则集, 这些规则集与可用于旧分析的规则集匹配:

- 设计
- 文档
- 可维护性
- 命名
- 性能
- 可靠性
- 安全性
- 用法

## <a name="see-also"></a>请参阅

- [分析器常见问题解答](analyzers-faq.md)
- [.NET Compiler Platform 分析器概述](roslyn-analyzers-overview.md)
- [安装分析器](install-roslyn-analyzers.md)
- [使用分析器](use-roslyn-analyzers.md)
- [使用规则集对代码分析规则进行分组](using-rule-sets-to-group-code-analysis-rules.md)
