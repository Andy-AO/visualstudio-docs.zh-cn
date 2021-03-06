---
title: 活动设计器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fae1b4905d66a5162591fd7c720ba81ed7ffda82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606611"
---
# <a name="while-activity-designer"></a>While 活动设计器

<xref:System.Activities.Statements.While> <xref:System.Activities.Statements.While.Body%2A> 当指定的条件的计算结果为**true**时，活动执行其中包含的活动。 包含的活动可能永远都不会执行。 如果希望所包含的活动至少执行一次，请改用 <xref:System.Activities.Statements.DoWhile> 活动。

## <a name="while-properties-in-workflow-designer"></a>工作流设计器中的 While 属性

下表列出最有用的 <xref:System.Activities.Statements.While> 活动属性并说明如何在设计器中使用它们。

|属性名称|必选|使用情况|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|错误|指定 <xref:System.Activities.Statements.While> 活动设计器在标头中的友好名称。 默认值为 While。 该值可以在 " **属性** " 窗口中编辑，也可以直接在活动设计器标头中编辑。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|
|<xref:System.Activities.Statements.While.Body%2A>|错误|包含 <xref:System.Activities.Statements.While.Condition%2A> 计算结果为 **true**时要执行的活动。|
|<xref:System.Activities.Statements.While.Condition%2A>|正确|包含 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 表达式，通过计算该表达式来确定是否要执行 <xref:System.Activities.Statements.While.Body%2A> 中的活动。|

## <a name="see-also"></a>另请参阅

- [控制流](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)