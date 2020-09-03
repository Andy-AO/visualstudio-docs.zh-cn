---
title: 选择域特定语言解决方案模板 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6522e3a1ad10f221f0ed7fc1761559ee9bc3f9b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668355"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>选择域特定语言解决方案模板
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要创建域特定语言解决方案，请选择特定于域的语言设计器向导中提供的解决方案模板之一。 通过选择与你要创建的语言最相似的模板，你可以最大程度地减少必须对起始解决方案进行的修改。

 特定于域的语言设计器向导中提供了以下解决方案模板。

> [!NOTE]
> 模板的用途是提供一个起始 DSL。 名为类和组件图的模板不是完整的 UML 关系图。 如果要创建 UML 模型，请考虑使用 UML 建模工具，该工具提供一组围绕单个模型集成的关系图。 这些关系图是可扩展的，并且可以使用 ModelBus 与你的 DSL 集成。 有关详细信息，请参阅为 [应用程序创建模型](../modeling/create-models-for-your-app.md)。

|模板|功能|说明|
|--------------|--------------|-----------------|
|类图|-隔离舱形状<br />-类继承<br />-关系继承<br />-形状继承<br />-关系属性|如果域特定语言包含具有属性的实体和关系，请使用此解决方案模板。 此模板创建类似于 UML 类图的域特定语言。 主要实体是类和接口，以及关联、通用化和实现关系。 类或接口显示为包含属性列表的框。|
|组件图|-端口|如果域特定语言包含组件（即软件系统的一部分），请使用此解决方案模板。 此模板创建类似于 UML 组件图的域特定语言。 主要实体是组件和端口，它们显示为组件外的小形状。|
|任务流关系图|-图像和几何形状<br />-   *泳道*|如果域特定语言包含工作流、状态或序列，请使用此解决方案模板。 此模板创建类似于 UML 活动图的域特定语言。 主要实体是活动，主关系是活动之间的转换。 该模板包括多个其他元素，如开始状态、最终状态和同步条。|
|最小语言|-一个类和形状<br />-一个关系和连接器|如果域特定语言不类似于其他模板，请使用此解决方案模板。 此模板创建一个具有两个类和一个关系的域特定语言，在 " **工具箱** " 中表示为 " **Box** " 和 " **线条**"。 类和每个关系都具有一个示例字符串属性。|
|最小 WinForm 设计器|-小型模型。<br />-显示模型的 Windows 窗体。|如果要构建一个应用程序，在该应用程序中，DSL 绑定到 Windows 窗体，而不是图形设计器，请使用此模板。<br /><br /> 用作语言的用户界面的窗体位于文件夹 Dsl\UI. 中。<br /><br /> 你应在打开窗体设计器之前生成项目。<br /><br /> 有关详细信息，请参阅 [创建基于 Windows 窗体的域特定语言](../modeling/creating-a-windows-forms-based-domain-specific-language.md)。|
|最小 WPF 设计器|-小型模型<br />-显示模型的 Windows Presentation Foundation 用户界面|如果要构建一个应用程序，在该应用程序中，DSL 绑定到 WPF 用户界面，而不是图形设计器，请使用此模板。<br /><br /> 用户界面的设计器位于文件夹 Dsl\UI. 中。<br /><br /> 你应在打开 UI 设计器之前生成项目。<br /><br /> 有关详细信息，请参阅 [创建基于 WPF 的域特定语言](../modeling/creating-a-wpf-based-domain-specific-language.md)。|
|DSL 库|-最小库|如果要生成可导入到其他 DSL 定义中的部分 DSL 定义，请使用此模板。|

## <a name="see-also"></a>另请参阅
 [域特定语言工具的概述](../modeling/overview-of-domain-specific-language-tools.md)
