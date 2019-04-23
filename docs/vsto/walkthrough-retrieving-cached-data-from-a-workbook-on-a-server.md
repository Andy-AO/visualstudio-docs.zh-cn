---
title: 演练：从一台服务器上的工作簿中检索缓存的数据
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd39ec744e88c2a9334f31c2974ed92f1f6b9a12
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101413"
---
# <a name="walkthrough-retrieve-cached-data-from-a-workbook-on-a-server"></a>演练：从一台服务器上的工作簿中检索缓存的数据
  本演练演示如何从 Microsoft Office Excel 工作簿中缓存而不启动 Excel 使用的数据集检索数据<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>类。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 本演练阐释了以下任务：

- 定义包含中的数据的数据集*AdventureWorksLT*数据库。

- 在 Excel 工作簿项目和控制台应用程序项目中创建数据集的实例。

- 创建<xref:Microsoft.Office.Tools.Excel.ListObject>这就是绑定到工作簿中的数据集和填充<xref:Microsoft.Office.Tools.Excel.ListObject>时打开工作簿的数据。

- 将工作簿中的数据集添加到数据缓存。

- 从控制台应用程序，而不启动 Excel 中的数据集到缓存的数据集的读取数据。

  尽管本演练假定您在开发计算机上运行代码，可以在没有安装 Excel 的服务器上使用本演练中所示的代码。

> [!NOTE]
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>系统必备
 你需要以下组件来完成本演练：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

- 对 Microsoft SQL Server 或 Microsoft SQL Server Express 的 AdventureWorksLT 示例数据库附加到它的运行中实例的访问权限。 您可以下载 AdventureWorksLT 数据库从[CodePlex 网站](http://go.microsoft.com/fwlink/?linkid=87843)。 有关附加数据库的详细信息，请参阅下列主题：

    - 若要通过使用 SQL Server Management Studio 或 SQL Server Management Studio Express 来附加数据库，请参阅[如何：附加数据库 (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database)。

    - 若要使用命令行中附加数据库，请参阅[如何：将数据库文件附加到 SQL Server Express](/previous-versions/sql/)。

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>创建一个类库项目定义数据集
 若要使用的 Excel 工作簿项目和控制台应用程序中的相同数据集，必须在单独的程序集引用的这两个这些项目中定义数据集。 在本演练中，在一个类库项目中定义数据集。

### <a name="create-the-class-library-project"></a>创建类库项目

1. 启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在 **“文件”** 菜单上，指向 **“新建”**，然后单击 **“项目”**。

3. 在模板窗格中，展开**Visual C#** 或**Visual Basic**，然后单击**Windows**。

4. 在项目模板列表中选择**类库**。

5. 在中**名称**框中，键入**AdventureWorksDataSet**。

6. 单击**浏览**，导航到你 *%UserProfile%\My Documents* （适用于 Windows XP 及更早版本） 或 *%UserProfile%\Documents* （适用于 Windows Vista) 文件夹，，然后单击**选择文件夹**。

7. 在中**新的项目**对话框框中，确保**创建解决方案目录**未选中复选框。

8. 单击 **“确定”**。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将添加**AdventureWorksDataSet**投影到**解决方案资源管理器**，并打开*Class1.cs*或者*Class1.vb*代码文件。

9. 在中**解决方案资源管理器**，右键单击*Class1.cs*或*Class1.vb*，然后单击**删除**。 此演练不需要此文件。

## <a name="define-a-dataset-in-the-class-library-project"></a>在类库项目中定义一个数据集
 定义用于 SQL Server 2005 包含 AdventureWorksLT 数据库中的数据的类型化数据集。 稍后在本演练中，将从 Excel 工作簿项目和控制台应用程序项目中引用此数据集。

 数据集*类型化数据集*表示 AdventureWorksLT 数据库的 Product 表中的数据。 有关类型化数据集的详细信息，请参阅[Visual Studio 中的数据集工具](../data-tools/dataset-tools-in-visual-studio.md)。

### <a name="define-a-typed-dataset-in-the-class-library-project"></a>在类库项目中定义的类型化数据集

1. 在中**解决方案资源管理器**，单击**AdventureWorksDataSet**项目。

2. 如果**数据源**窗口不可见，显示它，在菜单栏中选择**视图** > **其他 Windows**  >  **数据源**。

3. 选择 **“添加新数据源”** 以启动 **“数据源配置向导”**。

4. 单击“数据库” ，然后单击“下一步” 。

5. 如果具有现有连接到 AdventureWorksLT 数据库，选择此连接，然后单击**下一步**。

    否则，单击“新建连接” ，然后使用“添加连接”  对话框创建新连接。 有关详细信息，请参阅[添加新连接](../data-tools/add-new-connections.md)。

6. 在“将连接字符串保存到应用程序配置文件中”  页中，单击“下一步” 。

7. 在中**选择数据库对象**页上，展开**表**，然后选择**Product (SalesLT)**。

8. 单击 **“完成”**。

    *AdventureWorksLTDataSet.xsd*文件添加到**AdventureWorksDataSet**项目。 此文件定义以下各项：

   - 一个名为 `AdventureWorksLTDataSet`的类型化数据集。 此数据集表示 AdventureWorksLT 数据库中的产品表的内容。

   - 名为 TableAdapter `ProductTableAdapter`。 此 TableAdapter 可用于读取和写入数据中`AdventureWorksLTDataSet`。 有关详细信息，请参阅[TableAdapter 概述](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)。

     在本演练后面的部分中，你将使用这两个对象。

9. 在中**解决方案资源管理器**，右键单击**AdventureWorksDataSet**然后单击**生成**。

     验证此项目是否已生成且未发生错误。

## <a name="create-an-excel-workbook-project"></a>创建的 Excel 工作簿项目
 创建接口的数据的 Excel 工作簿项目。 稍后在本演练中，你将创建<xref:Microsoft.Office.Tools.Excel.ListObject>显示数据，并将数据集实例添加到工作簿中的数据缓存。

### <a name="create-the-excel-workbook-project"></a>创建 Excel 工作簿项目

1. 在中**解决方案资源管理器**，右键单击**AdventureWorksDataSet**解决方案，指向**添加**，然后单击**新项目**。

2. 在模板窗格中，展开 **“Visual C#”** 或 **“Visual Basic”**，然后展开 **“Office/SharePoint”**。

3. 在展开的 **“Office/SharePoint”** 节点下方，选择 **“Office 外接程序”** 节点。

4. 在项目模板列表中，选择 **“Excel 2010 工作簿”** 或 **“Excel 2013 工作簿”** 项目。

5. 在中**名称**框中，键入**AdventureWorksReport**。 未修改的位置。

6. 单击 **“确定”**。

     将打开“Visual Studio Tools for Office 项目向导”  。

7. 絋粄**创建一个新文档**已选中，然后单击**确定**。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 此时将打开**AdventureWorksReport**设计器中的工作簿，并添加**AdventureWorksReport**项目到**解决方案资源管理器**。

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>将数据集添加到 Excel 工作簿项目中的数据源
 可以在 Excel 工作簿中显示数据集之前，必须首先将数据集添加到 Excel 工作簿项目中的数据源。

1. 在中**解决方案资源管理器**，双击*Sheet1.cs*或*Sheet1.vb*下**AdventureWorksReport**项目。

     在设计器中打开工作簿。

2. 在 **“数据”** 菜单上，单击 **“添加新数据源”**。

     “数据源配置”向导随即打开。

3. 单击**对象**，然后单击**下一步**。

4. 在中**选择希望绑定对象**页上，单击**添加引用**。

5. 上**项目**选项卡上，单击**AdventureWorksDataSet** ，然后单击**确定**。

6. 下**AdventureWorksDataSet**的命名空间**AdventureWorksDataSet**程序集，单击**adventureworksltdataset** ，然后单击**完成**.

     **数据源**窗口将打开，并**adventureworksltdataset**添加到数据源的列表。

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>创建绑定到数据集的实例 ListObject
 若要在工作簿中显示数据集，请创建<xref:Microsoft.Office.Tools.Excel.ListObject>绑定到数据集的实例。 有关控件绑定到数据的详细信息，请参阅[将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)。

1. 在中**数据源**窗口中，展开**adventureworksltdataset**节点下的**AdventureWorksDataSet**。

2. 选择**产品**节点中，单击下拉箭头，然后选择**ListObject**下拉列表中。

     如果未显示的下拉箭头，确认工作簿是在设计器中打开。

3. 拖动**产品**到单元格 A1 的表。

     一个<xref:Microsoft.Office.Tools.Excel.ListObject>名为控件`productListObject`上工作表中，在单元格 A1 中开始创建。 同时，向项目添加了一个名为 `adventureWorksLTDataSet` 的数据集对象和一个名为 <xref:System.Windows.Forms.BindingSource> 的 `productBindingSource` 。 已将 <xref:Microsoft.Office.Tools.Excel.ListObject> 绑定到 <xref:System.Windows.Forms.BindingSource>，而后者又绑定到该数据集对象。

## <a name="add-the-dataset-to-the-data-cache"></a>将数据集添加到数据缓存
 若要启用外部 Excel 工作簿项目来访问该工作簿中的数据集的代码，必须将数据集添加到数据缓存。 数据缓存的详细信息，请参阅[缓存的文档级自定义项中的数据](../vsto/cached-data-in-document-level-customizations.md)并[缓存数据](../vsto/caching-data.md)。

1. 在设计器中，单击**adventureworksltdataset**。

2. 在中**属性**窗口中，将**修饰符**属性设置为**公共**。

3. 设置**CacheInDocument**属性设置为**True**。

## <a name="initialize-the-dataset-in-the-workbook"></a>初始化工作簿中的数据集
 可以从缓存的数据集检索数据，使用控制台应用程序之前，您必须首先填充缓存的数据集的数据。

1. 在中**解决方案资源管理器**，右键单击*Sheet1.cs*或*Sheet1.vb*文件，并单击**查看代码**。

2. 将 `Sheet1_Startup` 事件处理程序替换为以下代码。 此代码使用的实例`ProductTableAdapter`中定义的类**AdventureWorksDataSet**项目填充缓存的数据集数据，如果当前为空。

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>检查点
 生成并运行 Excel 工作簿项目，以确保它在编译和运行时没有错误。 此操作还会填充缓存的数据集，并将数据保存在工作簿中。

### <a name="build-and-run-the-project"></a>生成并运行项目

1. 在中**解决方案资源管理器**，右键单击**AdventureWorksReport**项目中，选择**调试**，然后单击**启动新实例**。

     生成该项目，并在 Excel 中打开工作簿。 验证以下内容：

    - <xref:Microsoft.Office.Tools.Excel.ListObject>用数据填充。

    - 中的值**ListPrice**的第一行的列<xref:Microsoft.Office.Tools.Excel.ListObject>是 1431.5。 在本演练后面将使用一个控制台应用程序，来修改中的值**ListPrice**列。

2. 保存该工作簿。 不要修改的文件的名称或工作簿的位置。

3. 关闭 Excel。

## <a name="create-a-console-application-project"></a>创建控制台应用程序项目
 创建一个控制台应用程序项目，用于修改中工作簿中缓存的数据集的数据。

1. 在中**解决方案资源管理器**，右键单击**AdventureWorksDataSet**解决方案，指向**添加**，然后单击**新项目**。

2. 在中**项目类型**窗格中，展开**Visual C#** 或**Visual Basic**，然后单击**Windows**。

3. 在中**模板**窗格中，选择**控制台应用程序**。

4. 在中**名称**框中，键入**DataReader**。 未修改的位置。

5. 单击 **“确定”**。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将添加**DataReader**投影到**解决方案资源管理器**，并打开*Program.cs*或者*Module1.vb*代码文件。

## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>使用控制台应用程序从缓存的数据集检索数据
 使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>类在控制台应用程序，以将数据读入本地`AdventureWorksLTDataSet`对象。 若要确认本地数据集使用缓存的数据集中的数据进行初始化，应用程序将显示在本地数据集中的行数。

### <a name="retrieve-data-from-the-cached-dataset"></a>从缓存的数据集检索数据

1. 在中**解决方案资源管理器**，右键单击**DataReader**项目，然后单击**添加引用**。

2. 上 **.NET**选项卡上，选择**microsoft.visualstudio.tools.applications.serverdocument 的引用**。

3. 单击 **“确定”**。

4. 在中**解决方案资源管理器**，右键单击**DataReader**项目，然后单击**添加引用**。

5. 上**项目**选项卡上，选择**AdventureWorksDataSet**，然后单击**确定**。

6. 打开*Program.cs*或*Module1.vb*代码编辑器中的文件。

7. 添加以下**使用**（适用于 C# 中) 或**导入**（适用于 Visual Basic 中) 到代码文件顶部的语句。

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. 将以下代码添加到 `Main` 方法中。 此代码声明了以下对象：

   - 实例`AdventureWorksLTDataSet`中定义的类型**AdventureWorksDataSet**项目。

   - AdventureWorksReport 工作簿中的生成文件夹的路径**AdventureWorksReport**项目。

   - 一个<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>要用来访问该工作簿中的数据缓存对象。

     > [!NOTE]
     >  以下代码假定使用保存工作簿 *.xlsx*扩展。 如果你的项目中的工作簿具有不同的扩展，可以修改根据需要路径。

     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]

9. 将以下代码添加到`Main`方法中上一步中添加的代码。 这段代码执行下列任务：

   - 它使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>属性的<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>类来访问工作簿中缓存的数据集。

   - 它读取从缓存的数据集到本地数据集中的数据。

   - 在本地数据集中，它显示行的数以确认它具有数据。

     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]

10. 上**构建**菜单上，单击**生成 DataReader**。

## <a name="test-the-project"></a>测试项目
 在运行控制台应用程序时，它将显示在本地数据集中的行数。

### <a name="test-the-workbook"></a>测试该工作簿

1. 在中**解决方案资源管理器**，右键单击**DataReader**项目，指向**调试**，然后单击**启动新实例**。

     验证应用程序报告本地数据集具有 295 行。

2. 按**Enter**关闭应用程序。

## <a name="next-steps"></a>后续步骤
 您可以了解有关使用缓存数据从下面这些主题的详细信息：

- 中缓存的数据集的数据更改而不启动 Excel。 有关详细信息，请参见[演练：更改服务器上的工作簿中的缓存的数据](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)。

## <a name="see-also"></a>请参阅

- [演练：将数据插入到的服务器上的工作簿](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
- [演练：更改服务器上的工作簿中的缓存的数据](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
