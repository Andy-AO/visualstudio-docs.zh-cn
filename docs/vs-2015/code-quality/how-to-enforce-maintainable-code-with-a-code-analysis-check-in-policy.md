---
title: 如何：使用代码分析签入策略强制实现代码的可维护性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d54ca9a31e8a1bbd2496bf8689a119e53580c79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660221"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>如何：使用代码分析签入策略强制实现代码的可维护性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

开发人员可以使用代码度量工具来度量其代码的复杂性和可维护性，但不能将代码度量值作为签入策略的一部分来调用。 但是，团队可以启用代码分析规则来验证其代码的符合性和代码度量标准，并通过签入策略强制执行这些规则。 有关代码度量值的详细信息，请参阅 [代码度量值](../code-quality/code-metrics-values.md)。

 开发人员可以通过代码分析签入策略来实现继承、类耦合、可维护性索引和复杂性规则的深度，从而强制实现代码的可维护性。 所有这四个规则都位于 "代码分析策略编辑器" 中的 "可维护性规则" 类别下。

 版本控制的管理员 [!INCLUDE[esprfound](../includes/esprfound-md.md)] 可以向签入策略要求添加代码分析可维护性规则。 这些签入策略要求开发人员在启动签入之前根据这些规则更改运行代码分析。

### <a name="to-open-the-code-analysis-policy-editor"></a>打开代码分析策略编辑器

1. 在 **团队资源管理器**中，右键单击团队项目，单击 " **团队项目设置**"，然后单击 " **源代码管理**"。

     此时将显示 " **源代码管理** " 对话框。

2. 在 " **签入策略** " 选项卡上，单击 " **添加**"。

     此时将显示 " **添加签入策略** " 对话框。

3. 在 " **签入策略** " 列表中，选择 " **代码分析** " 复选框，然后单击 **"确定"**。

     此时将显示 " **代码分析策略编辑器** " 对话框。

### <a name="to-enable-code-analysis-maintainability-rules"></a>启用代码分析可维护性规则

1. 在 " **代码分析策略编辑器** " 对话框中的 " **规则设置**" 下，展开 "可 **维护性规则** " 节点。

2. 选中以下规则的复选框：

    - 继承深度： **CA1501 AvoidExcessiveInheritance** -阈值：警告，深度超过5层

    - 复杂性： **CA1502 AvoidExcessiveComplexity** -阈值：警告（超过25个）

    - 可维护性索引： **CA1505 AvoidUnmaintainableCode** -阈值：警告低于20

    - 类耦合： **CA1506 AvoidExcessiveClassCoupling** -阈值：对于类超过80的警告，对于方法为30个以上

    - 此外，如果你希望规则冲突阻止生成，请选中规则说明旁边的 "将 **警告视为错误** " 复选框。

3. 单击" **确定**"。 新的签入策略现在适用于将来的签入。

## <a name="see-also"></a>另请参阅
 [代码度量值](../code-quality/code-metrics-values.md)[创建和使用代码分析签入策略](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
