---
title: 如何：使用导入设计器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f1c305129a7f46c8d1841f28d8084535ec7e4d9f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077571"
---
# <a name="how-to-use-the-imports-designer"></a>如何：使用导入设计器
导入设计器允许您为将在表达式中使用的类型输入命名空间。 更喜欢**导入**或**使用**Visual Basic.NET 和 C# 中，导入设计器中指定命名空间中的关键字使您能够只需进入您的表达式而不是完全限定的类型名称版本类型名称。  
  
 导入设计器既响应 UI 中的更改，也响应保存工作流时进行的更改。 保存工作流后，会向导入设计器中自动添加命名空间。 其中包括：  
  
- 变量和自变量声明中使用的所有类型的命名空间。  
  
- 表达式中使用的所有类型的命名空间。  
  
- 序列化工作流所需的其他任何命名空间（例如，放置在工作流中的自定义活动所使用的命名空间）。  
  
  保存工作流时，您可能会注意到您已手动删除的某些命名空间可能会由于上述列表中描述的逻辑自动重新添加到导入设计器中。  
  
### <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>向导入的命名空间列表中添加命名空间  
  
1. 在 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 或重新承载的工作流应用程序中，打开一个 WCF 工作流服务应用程序、工作流控制台应用程序或活动库项目。  
  
2. 单击**导入**主画布的底部。 此时将显示导入设计器。  
  
3. 输入或从导入设计器顶部的下拉列表控件中选择一个命名空间。  
  
     您键入时，会显示与键入的字符匹配的有效命名空间列表。  
  
4. 按**Enter**将命名空间添加到列表。  
  
5. 如果你想要从列表中删除一个命名空间，选择的命名空间，然后按**删除**键盘上键。 请注意如果命名空间因为任何原因（例如，项目不再引用包含命名空间的程序集）而无效，只能删除它。