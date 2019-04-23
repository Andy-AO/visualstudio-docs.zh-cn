---
title: 从现有的 SharePoint 网站导入项 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.SelectionDependency
- VS.SharepointTools.WSPImport.SpecifyProjectSource
- VS.SharePointTools.WSPImport.SelectionItemsToImport
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, importing .wsp files
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 206cd77ae3c648add62b17c86a4966e6174c345c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082576"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>从现有的 SharePoint 网站导入项目
  利用“导入 SharePoint 解决方案包”项目模板，你可以在新的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 解决方案中重用现有 SharePoint 网站中的元素，例如，内容类型和字段。 虽然无需修改即可运行大多数导入的解决方案，但需要考虑一些限制和问题，尤其是在导入任何项后对这些项进行修改的情况下。

> [!NOTE]
>  若要导入可重用工作流，请使用“导入可重用工作流”项目模板。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [导入可重用工作流的准则](../sharepoint/guidelines-for-importing-reusable-workflows.md)。

## <a name="supported-sharepoint-solutions"></a>受支持的 SharePoint 解决方案
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] 完全支持导入在 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] 和 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]中创建的解决方案。

 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] 不支持导入在以下应用程序中创建的解决方案：

- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]

- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]

- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]

- Microsoft SharePoint Designer 2007

- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]

  虽然通常可以成功导入由这些应用程序创建的解决方案，但该功能未经测试且不受支持。

## <a name="item-import-restrictions"></a>项导入限制
 尽管可以从现有导入大多数 SharePoint 项 *.wsp*文件中，以下各项不受支持，可能需要进行修改才能正常工作：

- BDC 实体

- 代码工作流关联元素

- 代码工作流

- 可视 Web 部件 (.ascx)

- Web 服务 (*.asmx*)

- 内容类型绑定

- 事件接收器

- 列表定义（模板）

- 网站定义

  从解决方案的导出时[!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)]或[!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]，这些项将自动从排除 *.wsp*文件。 但是，其他 *.wsp*从不受支持的工具生成的文件可能包含这些项。 （请参阅本主题前面的“支持的 SharePoint 解决方案”。）

## <a name="what-happens-when-you-import-a-solution"></a>导入解决方案时，会发生什么情况
 当导入使用导入 SharePoint 解决方案包模板时，解决方案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将所有的内容复制 *.wsp*导入文件和尝试协调和保留尽可能多的关联和之间的引用元素和尽可能及其文件。

 所有导入的项将复制到“解决方案资源管理器” 中对应的文件夹。 例如，内容类型出现在“内容类型”  文件夹下，列表实例出现在“列表实例” 下。 与导入的项关联的文件也将复制到该项的文件夹中。 例如，导入的列表实例包括其模块、窗体和 ASPX 页。

### <a name="dependent-items"></a>依赖项
 如果在“导入 SharePoint 解决方案包”向导中选择某一项，但没有选择其依赖项，则将显示一个消息框，通知你导入之前还必须选择相应的依赖项。

### <a name="what-are-features"></a>功能有哪些？
 SharePoint Designer 用户可能会看到一些称作 *功能*的意想不到的文件出现在“解决方案资源管理器”  中的导入的解决方案中。虽然功能过去就存在于 SharePoint Designer 解决方案中，但它们是隐藏的。 现在，功能在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中是可见的。

 功能是包含 SharePoint 项的容器。 每个功能都会保留对它所包含的每个项（如内容类型和列表定义）的引用。 在导入解决方案时， [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将设置所有导入元素的功能，并尝试保留这些文件的功能与元素间的关系。 所有未能解析其引用的文件都将置于“其他已导入文件”  文件夹中。

 有关功能的详细信息，请参阅[开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)并[使用功能](http://go.microsoft.com/fwlink/?LinkID=147704)。

### <a name="handle-special-cases"></a>处理特殊情况
 在某些情况下，Visual Studio 无法协调项及其依赖文件。 所有 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 未能解析的文件都将出现在“其他已导入文件” 文件夹下。 此外，这些文件的“DeploymentType”  属性将设置为“NoDeployment”  ，以便它们不会随解决方案一起部署。

 例如，如果您导入列表定义 ExpenseForms，则具有该名称的列表定义将显示在**列出定义**中的文件夹**解决方案资源管理器**连同其*Elements.xml*并*Schema.xml*文件。 但其关联的 ASPX 和 HTML 窗体可能会放置在“其他已导入文件”  文件夹下的名为“ExpenseForms”  的文件夹中。 若要完成此导入，请在“解决方案资源管理器”  中的 ExpenseForms 列表定义下移动这些文件，并将每个文件的“DeploymentType”  属性从“NoDeployment”  更改为“ElementFile” 。

 当导入事件接收器*Elements.xml*文件复制到正确的位置，但您必须手动将程序集包含解决方案包，以便它将部署的解决方案。 [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)] 如何执行此操作，请参阅[如何：添加和删除其他程序集](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。

 在导入工作流时，InfoPath 窗体将会复制到“其他已导入文件”  文件夹中。 如果 *.wsp*文件包含 Web 模板，它被设置为中的启动页**解决方案资源管理器**。

## <a name="import-fields-and-property-bags"></a>导入字段和属性包
 导入具有多个字段的解决方案时，所有单独的字段定义将合并到单个*Elements.xml*中的节点下的文件**解决方案资源管理器**调用**字段**. 同样，所有属性包项将都合并到*Elements.xml*调用节点下的文件**PropertyBags**。

 SharePoint 中的字段是指定数据类型（如文本、布尔值或查阅）的列。 有关详细信息，请参阅[构建基块：列和字段类型](http://go.microsoft.com/fwlink/?LinkId=182304)。 利用属性包，可以向 SharePoint 中的对象（从场到 SharePoint 网站上的列表的所有内容）添加属性。 属性包将作为属性名和属性值的哈希表实现。 有关详细信息，请参阅 [管理 SharePoint 配置](http://go.microsoft.com/fwlink/?LinkId=182296) 或 [SharePoint 属性包设置](http://go.microsoft.com/fwlink/?LinkId=182297)。

## <a name="delete-items-in-the-project"></a>删除项目中的项
 SharePoint 解决方案中的大多数项都具有一个或多个依赖项。 例如，列表实例依赖于内容类型，而内容类型依赖于字段。 导入 SharePoint 解决方案后，如果你删除此解决方案中的某个项而不删除其依赖项，则在你尝试部署解决方案之前， [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 不会告知你任何引用问题。 例如，如果导入的解决方案具有的列表实例依赖某个内容类型，而你删除了该内容类型，则在部署时可能会出现错误。 如果 SharePoint 服务器中不存在此依赖项，则会发生错误。 同样，如果已删除的项也具有关联的属性包，然后删除这些属性包项从**PropertyBags** *Elements.xml*文件。 因此，如果从导入的解决方案中删除任何项，并且存在部署错误，则应检查是否还需要删除任何依赖项。

## <a name="restore-missing-feature-attributes"></a>还原缺少的功能属性
 在导入解决方案时，将从导入的功能清单中略去一些可选的功能属性。 如果你想要还原这些属性在新的功能文件中，标识缺少属性： 将原始功能文件与新的功能清单进行比较，并按照本主题中的说明[如何：自定义 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)。

## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>不对内置列表实例执行部署冲突检测
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 不对内置列表实例（即，SharePoint 附带的默认列表实例）执行部署冲突检测。 不执行冲突检测是为了避免覆盖 SharePoint 上的内置列表实例。 仍将部署或更新内置列表实例，但不会对其进行删除或覆盖。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [SharePoint 打包和部署进行故障排除](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)。

## <a name="import-sharepoint-server-2010-workflows"></a>导入 SharePoint Server 2010 工作流
 如果导入在 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]中创建的工作流，则此工作流在部署后将不会正确运行。 此工作流无法正确运行的原因是，缺少某些程序集且  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] 工作流包含 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 工作流解决方案目前不支持的 InfoPath 窗体。 不过，在修复一些项后（如添加对 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] 程序集的引用并重新连接 InfoPath 窗体），可以使已导入的 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] 工作流正确工作。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [导入 SharePoint Server 2010 工作流](http://go.microsoft.com/fwlink/?LinkId=182226).

## <a name="item-name-character-limit"></a>项名称字符限制
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将项目和项目项名称（包括路径）限制为总共 260 个字符。 在导入解决方案时，如果项名称超出此限制，则会收到错误：

 **指定的路径、 文件名，或两者都太长。完全限定文件名必须少于 260 个字符，而目录名必须少于 248 个字符。**

 若收到此错误，则不会创建相应的项。 导入的模块最常出现此问题。 若要避免此问题，请执行下列操作：

- 在“添加新项目”  对话框中输入项目名称时，请使用项目的短名称。

- 在尽可能接近根文件夹的位置创建项目，以便减小路径长度。

## <a name="the-sharepointproductversion-attribute"></a>SharePointProductVersion 属性
 如果导入在早期版本的 SharePoint（如 [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] 或 [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]）中创建的解决方案，请将包清单中的 SharePointProductVersion 属性值更改为 12.0，或将脚本管理器控件插入到所有导入的网页中并将 SharePointProductVersion 属性值保持为 14.0。 否则，导入的 Web 窗体将不会显示在 SharePoint 中。

### <a name="background"></a>背景
 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] 和 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] 中的解决方案包含一个名为 SharePointProductVersion 的属性。 SharePoint 在其包清单中使用此属性来确定为其设计解决方案的 SharePoint 的版本。 两个有效值为 12.0 和 14.0。 值 12.0 指示为 [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] 或 [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]设计该项；值 14.0 指示为 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] 或 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]设计该项。

 为了在呈现 ASPX 页时增强安全性， [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] 和 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] 要求所有 ASPX 页或母版页包含脚本管理器控件。 有关脚本管理器的详细信息，请参阅 [ScriptManager 控件概述](http://go.microsoft.com/fwlink/?LinkID=169399)。 由于 [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] 和 [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]中未提供脚本管理器控件，因此必须向升级为 [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] 或 [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] 的任意 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] 或 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]页中添加一个脚本管理器控件。 使用标准母版页的 ASPX 页不需要脚本管理器控件，因为已向标准母版页中添加了一个脚本管理器控件。 但是，未使用母版页的 ASPX 页或使用自定义母版页的 ASPX 页必须添加脚本控件，以便在 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] 或 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]中工作。

 在将 [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] 或 [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] 项目导入到 [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]中时，缺少脚本管理器控件可能会导致出现问题，因为所有新项目的 SharePointProductVersion 属性都被设置为 14.0。 如果部署的已升级项目具有一个不带脚本管理器的 Web 窗体，则该窗体将不会在 SharePoint 中显示。

## <a name="see-also"></a>请参阅
- [演练：从现有的 SharePoint 网站导入项目](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)
- [导入可重用工作流的准则](../sharepoint/guidelines-for-importing-reusable-workflows.md)
- [演练：导入 Visual Studio SharePoint Designer 可重用工作流](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
- [如何：将现有 BDC 模型文件添加到 SharePoint 项目](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
