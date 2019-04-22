---
title: 与 XML 编辑器的集成 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 350b97385ab03daca80cc86d4f672dfec07222aa
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654017"
---
# <a name="integration-with-xml-editor"></a>与 XML 编辑器的集成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 编辑器中集成了 XML 架构设计器。 如果您修改 XSD 文件在 XML 编辑器中，更改将反映在[XML 架构资源管理器](../xml-tools/xml-schema-explorer.md)。 如果有[关系图视图](../xml-tools/graph-view.md)或[内容模型视图](../xml-tools/content-model-view.md)打开，更改也会反映在存在。 可通过以下方法在 XML 架构设计器和 XML 编辑器之间导航：  
  
- 在 XML 编辑器中，右键单击某个节点并选择**在 XML 架构资源管理器中显示**。  
  
- 在关系图视图和 XML 架构资源管理器中，双击某个节点，或右键单击某个节点并选择**查看代码**。 在内容模型视图中，右键单击某个节点并选择**查看代码**。  
  
  以下屏幕快照显示了在 XML 架构资源管理器中打开的 XML 架构。 XML 架构资源管理器在树视图中显示架构集。 XML 编辑器显示当前在 XML 架构资源管理器中处于活动状态的节点的文本视图。  
  
  ![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif "XSDDesignerWithXMLEditor")  
  
  有时，在 XML 编辑器中和在图形设计器中并行查看代码是很有帮助的。 若要同时查看这两个文件，请右键单击任意位置在 XML 编辑器中，并选择**视图设计器**。 在 Visual Studio Windows 菜单中，选择**新水平 （或垂直） 选项卡组**。  
  
  ![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif "XSDDesignerWithXMLEditorAndCMV")  
  
## <a name="see-also"></a>请参阅  
 [XML 架构资源管理器](../xml-tools/xml-schema-explorer.md)
