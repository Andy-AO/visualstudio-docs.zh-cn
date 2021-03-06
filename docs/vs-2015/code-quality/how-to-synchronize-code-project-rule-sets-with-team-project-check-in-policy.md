---
title: 如何：将代码项目规则集与团队项目签入策略同步 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3c6e7550940f9d2efa5ca228123310f1b861ee76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651604"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>如何：将代码项目规则集与团队项目签入策略同步
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

通过指定至少包含签入策略规则集中指定规则的规则集，可以将代码项目的代码分析设置同步到团队项目的签入策略。 开发人员主管可以通知您此签入策略的规则集的名称和位置。 您可以使用下列选项之一来确保项目的代码分析使用正确的规则集：

- 如果签入策略使用 Microsoft 内置规则集之一，请打开代码项目的 "属性" 对话框，显示 "代码分析" 页，然后在代码项目设置的 "代码分析" 页上选择规则集。 Microsoft 标准规则集随 Visual Studio 一起自动安装为只读，不应进行编辑。 如果未编辑规则集，则保证策略和本地规则集中的规则匹配。

- 如果签入策略使用自定义规则集，请对版本控制中的规则集文件执行 get 操作，以创建本地副本。 然后在代码项目的代码分析设置中指定本地位置。 如果签入策略的规则集是最新的，则确保规则匹配。

     如果将版本控制位置映射到与你的代码项目具有相同关系的本地文件夹，则使用相对路径设置规则的位置。 相对路径可确保代码分析的代码项目设置可移至其他计算机。

- 为代码项目的签入策略自定义规则集的副本。 请确保新规则集包含签入策略中的所有规则以及要包括的任何其他规则。 您必须确保规则集包含签入策略规则集中的所有规则。

### <a name="to-specify-a-microsoft-standard-rule-set"></a>指定 Microsoft 标准规则集

1. 在 **解决方案资源管理器**中，右键单击代码项目，然后单击 " **属性**"。

2. 单击“代码分析”。

3. 在 " **运行此规则集** " 列表中，单击 "签入策略规则集"。

### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>指定自定义签入策略规则集

1. 如有必要，对指定签入策略的规则集文件执行 get 操作。

2. 在 **解决方案资源管理器**中，右键单击代码项目，然后单击 " **属性**"。

3. 单击“代码分析”。

4. 在 " **运行此规则集** " 列表中，单击 "" **\<Browse...>** 。

5. 在 " **打开** " 对话框中，指定签入策略规则集文件。

### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>为代码项目创建自定义规则集

1. 按照本主题前面的过程之一，在 "项目设置" 对话框的 "代码分析" 页上选择团队项目的签入策略。

2. 单击“打开”。

3. 使用规则集编辑器添加或删除规则。

     有关详细信息，请参阅 [创建自定义规则集](../code-quality/creating-custom-code-analysis-rule-sets.md)。

4. 将修改后的规则集保存到本地计算机上的规则集文件或 UNC 路径。

5. 打开代码项目的 "属性" 对话框，并显示 " **代码分析** " 页。

6. 在 " **运行此规则集** " 列表中，单击 "" **\<Browse...>** 。

7. 在 " **打开** " 对话框中，指定规则集文件。
