---
title: RemoveFromCollection &lt; T &gt; 活动设计器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ac088c6e5710fcd1b7c401402ad473488f89524
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672567"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>RemoveFromCollection &lt; T &gt; 活动设计器
" **RemoveFromCollection \<T> ** " 活动设计器用于创建和配置 <xref:System.Activities.Statements.RemoveFromCollection%601> 活动。

## <a name="the-removefromcollectiont-activity"></a>RemoveFromCollection \<T> 活动
 <xref:System.Activities.Statements.RemoveFromCollection%601> 活动从特定集合中移除指定项。

### <a name="using-the-removefromcollectiont-activity-designer"></a>使用 RemoveFromCollection \<T> 活动设计器
 " **RemoveFromCollection \<T> ** " 活动设计器可在 "**工具箱**" 的 "**集合**" 类别中找到，可通过单击 (上的 "**工具箱**" 选项卡访问，也可以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 从 "**视图**" 菜单中选择 "**工具栏**" 或按 CTRL + ALT + X。 ) 

 可以将 " **RemoveFromCollection \<T> ** " 活动设计器从 "**工具箱**" 拖放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 图面上通常放置活动的任何位置，例如中 <xref:System.Activities.Statements.Sequence> 。 这将创建一个 <xref:System.Activities.Statements.RemoveFromCollection%601> 活动，其默认值为 <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection \<Int32> 。 <xref:System.Activities.Activity.DisplayName%2A>可以在 " ** \<T> RemoveFromCollection** " 活动设计器的标头中或在属性网格的 " **DisplayName** " 框中编辑值。 其他属性必须在属性网格上编辑。

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection \<T> 属性
 下表列出 <xref:System.Activities.Statements.RemoveFromCollection%601> 属性并说明如何在设计器中使用它们。

|属性名称|必选|使用情况|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|错误|<xref:System.Activities.Statements.RemoveFromCollection%601> 活动的可选友好名称。 默认值为 RemoveFromCollection \<Int32> 。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|正确|要添加到**集合 \<T> **中的项。 此项的类型为 *T*，类型为 *TypeArgument*。 若要指定项，请在属性网格中键入 Visual Basic 表达式。|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|正确|项应添加到的集合。 此集合的类型为 **ICollection \<TypeArgument> 。** 若要指定集合，请在属性网格中键入 Visual Basic 表达式。|
|*TypeArgument*|正确|包含在 <xref:System.Collections.Generic.ICollection%601> 中的项的类型 T。 默认情况下，此 *TypeArgument* 类型设置为 **Int32**。 若要更改类型，请在属性网格的组合框中更改 " *TypeArgument* " 的值。|
|<xref:System.Activities.Activity%601.Result%2A>|错误|一个指示指定项是否已从集合中移除的值。 若要指定要绑定到结果的变量，请在属性网格中键入一个变量。|

## <a name="see-also"></a>另请参阅
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md)