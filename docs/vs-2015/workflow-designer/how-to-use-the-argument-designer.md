---
title: 如何：使用自变量设计器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c9ea40a2af8139895a49c993588555f06bfda7f5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60090701"
---
# <a name="how-to-use-the-argument-designer"></a>如何：使用参数设计器
与以前版本的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 相比，该参数设计器使数据流入和流出某个活动更容易。 通过单击来访问在设计器**自变量**设计画布左下角的按钮。 在设计器包含一系列参数显示在表格窗体，可以按每一列标题排序除外**默认值**列。 每个自变量都包含名称、输入/输出/输入-输出/属性方向、类型和默认表达式值（如果有）。 名称和默认的表达式值都是可编辑的文本字段，类型和方向是下拉项。 [!INCLUDE[crabout](../includes/crabout-md.md)] 自变量，请参阅[变量和自变量](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)。  
  
### <a name="to-create-a-new-argument"></a>创建新自变量  
  
1. 在 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 中打开一个工作流或活动解决方案。  
  
2. 通过单击打开自变量设计器**自变量**设计画布左下角的按钮。 此时将显示参数设计器。  
  
3. 单击标记为空的行**创建自变量**。 这会将新行添加使用新的自变量，使用以下默认值： 为 argumentx**名称**其中 x 是一个整数，其初始值为 1 来创建唯一的参数名称，将自动递增**中**有关**方向**，和**字符串**有关**自变量类型**。 为添加任何值**默认值**。 可以在工作流设计过程中随时更改这些值。  
  
    > [!NOTE]
    >  若要删除参数，通过单击选择该参数，然后按**删除**密钥。  
  
## <a name="see-also"></a>请参阅  
 [使用工作流设计器](../workflow-designer/using-the-workflow-designer.md)   
 [变量和参数](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)