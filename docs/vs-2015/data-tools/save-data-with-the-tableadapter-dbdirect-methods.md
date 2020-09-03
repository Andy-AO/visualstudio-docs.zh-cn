---
title: 通过 TableAdapter DBDirect 方法保存数据 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce987f5ef90448c41da45a39c62710b968e11199
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655423"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>用 TableAdapter DBDirect 方法保存数据
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本演练通过使用 TableAdapter 的 DBDirect 方法，为直接针对数据库运行 SQL 语句提供了详细说明。 TableAdapter 的 DBDirect 方法可对数据库更新进行精确的控制。 您可以使用这些方法来运行特定的 SQL 语句和存储过程，方法是根据 `Insert` 应用 (程序的需要调用单独的、 `Update` 和方法，而不是 `Delete` `Update` 在一次调用中执行 UPDATE、INSERT 和 DELETE 语句) 的重载方法。

 在本演练中，你将学会如何执行以下任务：

- 创建新的 **Windows 应用程序**。

- 使用 " [数据源配置向导](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)" 创建和配置数据集。

- 选择从“数据源”窗口拖动某些项时要在窗体上创建的控件****。 有关详细信息，请参阅 [设置在从 "数据源" 窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

- 通过将某些项从“数据源”窗口拖到窗体上来创建数据绑定窗体****。

- 添加方法以直接访问数据库，并执行插入、更新和删除操作。

## <a name="prerequisites"></a>先决条件
 若要完成本演练，你将需要：

- 能够访问 Northwind 示例数据库。

## <a name="create-a-windows-application"></a>创建 Windows 应用程序
 第一步是创建 **Windows 应用程序**。

#### <a name="to-create-the-new-windows-project"></a>创建新的 Windows 项目

1. 在 Visual Studio 中的 " **文件** " 菜单上，创建一个新 **项目**。

2. 将项目命名为 **TableAdapterDbDirectMethodsWalkthrough**。

3. 选择 " **Windows 应用程序**"，然后选择 **"确定"**。 有关详细信息，请参阅 [客户端应用程序](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。

     创建“TableAdapterDbDirectMethodsWalkthrough”项目并将其添加到“解决方案资源管理器”中********。

## <a name="create-a-data-source-from-your-database"></a>从数据库创建数据源
 此步骤根据 Northwind 示例数据库中的 `Region` 表，使用“数据源配置”向导创建数据源****。 你必须具有对 Northwind 示例数据库的访问权限，才能创建连接。

#### <a name="to-create-the-data-source"></a>创建数据源

1. 在 " **数据** " 菜单上，选择 " **显示数据源**"。

2. 在“数据源”窗口，选择“添加新数据源”以启动“数据源配置”向导************。

3. 在 " **选择数据源类型** " 屏幕上，选择 " **数据库**"，然后选择 " **下一步**"。

4. 在 " **选择你的数据连接** " 屏幕上，执行以下操作之一：

    - 如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。

         - 或 -

    - 选择“新建连接”以启动“添加/修改连接”对话框********。

5. 如果数据库需要密码，请选择该选项以包括敏感数据，然后选择 " **下一步**"。

6. 在 "将 **连接字符串保存到应用程序配置文件** " 屏幕上，选择 " **下一步**"。

7. 在 " **选择数据库对象** " 屏幕上，展开 " **表** " 节点。

8. 选择 `Region` 该表，然后选择 " **完成**"。

     将“NorthwindDataSet”添加到项目后，“数据源”窗口中即会显示 `Region` 表********。

## <a name="addcontrols-to-the-form-to-display-the-data"></a>Addcontrols 显示数据的窗体
 通过将某些项从“数据源”窗口拖到窗体上来创建数据绑定控件****。

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>在 Windows 窗体上创建数据绑定控件

- 将 "主 **区域** " 节点从 " **数据源** " 窗口拖到窗体上。

     用于导航记录的 <xref:System.Windows.Forms.DataGridView> 控件和工具栏（<xref:System.Windows.Forms.BindingNavigator>）将显示在窗体上。 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md) <xref:System.Windows.Forms.BindingSource> 组件栏中出现 NorthwindDataSet、RegionTableAdapter、和 <xref:System.Windows.Forms.BindingNavigator> 。

#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>添加将调用单个 TableAdapter DbDirect 方法的按钮

1. 将三个 <xref:System.Windows.Forms.Button> 控件从“工具箱”拖到“Form1”上（在“RegionDataGridView”的下面）************。

2. 在每个按钮上设置下列“名称”和“文本”属性********。

    |名称|文本|
    |----------|----------|
    |`InsertButton`|**插入**|
    |`UpdateButton`|**Update**|
    |`DeleteButton`|**删除**|

#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>添加将新记录插入数据库所使用的代码

1. 选择 " **InsertButton** " 以创建 click 事件的事件处理程序，并在代码编辑器中打开窗体。

2. 用下面的代码替换 `InsertButton_Click` 事件处理程序：

     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]

#### <a name="to-add-code-to-update-records-in-the-database"></a>添加更新数据库中的记录所使用的代码

1. 双击“UpdateButton”以创建 Click 事件的事件处理程序，并在代码编辑器中打开窗体****。

2. 用下面的代码替换 `UpdateButton_Click` 事件处理程序：

     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]

#### <a name="to-add-code-to-delete-records-from-the-database"></a>添加代码以从数据库中删除记录

1. 选择 " **DeleteButton** " 以创建 click 事件的事件处理程序，并在代码编辑器中打开窗体。

2. 用下面的代码替换 `DeleteButton_Click` 事件处理程序：

     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]

## <a name="run-the-application"></a>运行此应用程序

#### <a name="to-run-the-application"></a>要运行应用程序

- 选择 **F5** 以运行应用程序。

- 选择 " **插入** " 按钮，并验证新记录是否显示在网格中。

- 选择 " **更新** " 按钮，并验证是否已在网格中更新记录。

- 选择 " **删除** " 按钮，并验证是否已从网格中删除该记录。

## <a name="next-steps"></a>后续步骤
 根据应用程序的要求，在创建数据绑定窗体后，你可能想要执行几个步骤。 你可以通过以下操作来增强此演练的效果：

- 将搜索功能添加到该窗体。 有关详细信息，请参阅 [如何：将参数化查询添加到 Windows 窗体应用程序](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416)。

- 通过从“数据源”窗口中选择“使用向导配置数据集”，将其他表添加到数据集中********。 可以通过将相关节点拖到窗体上来添加显示相关数据的控件。

## <a name="see-also"></a>另请参阅
 [将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)
