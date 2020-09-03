---
title: FlowDecision 活动设计器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b93d88462d5e3984b06c671455439e9bd2b07c5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656688"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision 活动设计器
<xref:System.Activities.Statements.FlowDecision> 节点是一个条件节点，它根据指定条件是否成立来将控制流分支到两个备分支之一。 如果流需要的分支超过两个，请改用 <xref:System.Activities.Statements.FlowSwitch%601>。

## <a name="the-flowdecision-node"></a>FlowDecision 节点
 当流可以分支到两条路径时可使用 <xref:System.Activities.Statements.FlowDecision>。 一个 <xref:System.Activities.Statements.FlowDecision> 节点具有一个 <xref:System.Activities.Statements.FlowDecision.Condition%2A>，并且两个可能结果中的每一个都有一个关联的 <xref:System.Activities.Statements.FlowNode>，这两个可能的结果为：<xref:System.Activities.Statements.FlowDecision.True%2A> 和 <xref:System.Activities.Statements.FlowDecision.False%2A>。 将对 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 进行计算，此计算值决定要在 <xref:System.Activities.Statements.FlowNode> 中处理的下一个 <xref:System.Activities.Statements.Flowchart>。

### <a name="using-the-flowdecision-designer"></a>使用 FlowDecision 设计器
 **FlowDecision**设计器可在 "**工具箱**" 的 "**流程图**" 类别中找到，可通过单击 (上的 "**工具箱**" 选项卡， [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或者从 "**视图**" 菜单中选择 "**工具栏**" 或按 CTRL + ALT + X 来访问。 ) 

 可以将 " **FlowDecision** " 设计器从 " **工具箱** " 拖放到图面上的 " [!INCLUDE[wfd2](../includes/wfd2-md.md)] **流程图** " 活动设计器中。 这会在 <xref:System.Activities.Statements.FlowDecision> 活动中创建标记为的 **决策** <xref:System.Activities.Statements.Flowchart> 。 将鼠标悬停在设计器上，将显示两个分支的 **True** 和 **False** 方控点。

 将 **FlowDecision** 设计器和其他设计器拖到 **Flowchart**后，可将节点链接在一起以指定执行顺序。 若要在源节点 (**) 和目标**节点之间创建链接**False** ，请将鼠标**FlowDecision**悬停在源节点的设计器上，并在其每一侧显示正方形控点。 单击这些正方形处理框之一并按下鼠标按钮将其拖到当鼠标悬停在目标节点上时该节点周围以类似方式显示的处理框之一。 松开鼠标按钮，此时将在这两个节点之间创建一个链接，表示为从源设计器指向目标设计器的箭头。

 <xref:System.Activities.Statements.FlowDecision.Condition%2A>通过单击提示文本 "输入 VB 表达式" 的位置，可以在 "**属性**" 窗口的 "**条件**" 框中键入指示的表达式。

### <a name="the-flowdecision-properties"></a>FlowDecision 属性
 下表列出 <xref:System.Activities.Statements.FlowDecision> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中或设计器图面上进行编辑。

|属性名称|必选|使用情况|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|正确|确定流控制所采用的路径的条件。|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|错误|<xref:System.Activities.Statements.FlowDecision.Condition%2A> 成立时流控制所采用的路径。|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|错误|<xref:System.Activities.Statements.FlowDecision.Condition%2A> 不成立时流控制所采用的路径。|

## <a name="see-also"></a>另请参阅
 [流程图](../workflow-designer/flowchart-activity-designers.md) [Flowchart](../workflow-designer/flowchart-activity-designer.md) [FlowSwitch \<T> ](../workflow-designer/flowswitch-t-activity-designer.md)