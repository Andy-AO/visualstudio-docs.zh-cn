---
title: 如何：使用主机控件中的数据更新数据源
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d1e7bfd074b0ed7f6f1bcef99acf28f478a9c51
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097487"
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>如何：使用主机控件中的数据更新数据源
  可以将宿主控件绑定到数据源，然后使用在此控件中对数据所做的更改来更新该数据源。 此过程包括以下两个主要步骤：

1. 使用控件中的已修改数据更新内存中数据源。 通常情况下，内存中数据源是一个 <xref:System.Data.DataSet>、 <xref:System.Data.DataTable>或某个其他数据对象。

2. 使用内存中数据源中的已更改数据更新数据库。 此步骤仅适用于数据源连接到后端数据库（例如 SQL Server 或 Microsoft Office Access 数据库）的情况。

   有关主机控件和数据绑定的详细信息，请参阅[主机项和主机控件概述](../vsto/host-items-and-host-controls-overview.md)并[将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)。

   [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="update-the-in-memory-data-source"></a>更新内存中数据源
 默认情况下，支持简单数据绑定的宿主控件（例如 Word 文档中的内容控件或 Excel 工作表中的命名范围控件）不将数据更改保存到内存中数据源。 也就是说，如果最终用户更改宿主控件中的某个值后离开此控件，则该控件中的这个新值并不会自动保存到数据源中。

 若要将数据保存到数据源，可以编写代码来更新数据源以响应特定事件在运行时，或可以配置要在控件中的值更改时自动更新数据源的控件。

 无需将 <xref:Microsoft.Office.Tools.Excel.ListObject> 更改保存到内存中数据源。 如果将 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件绑定到数据，则 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件会自动将更改保存到内存中数据源，而无需借助其他代码。

### <a name="to-update-the-in-memory-data-source-at-runtime"></a>若要更新在运行时的内存中数据源

- 调用将控件绑定到数据源的 <xref:System.Windows.Forms.Binding.WriteValue%2A> 对象的 <xref:System.Windows.Forms.Binding> 方法。

     下面的示例将在 Excel 工作表中对 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件所做的更改保存到数据源。 此示例假定你有一个名为 <xref:Microsoft.Office.Tools.Excel.NamedRange> 的 `namedRange1` 控件，且其 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 属性已绑定到数据源中的一个字段。

     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]

### <a name="automatically-update-the-in-memory-data-source"></a>自动更新内存中数据源
 你可也可以配置控件，使其自动更新内存中数据源。 在文档级项目中，可以通过使用代码或设计器来实现。 在 VSTO 外接程序项目中，您必须使用代码。

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>通过使用代码将控件设置为自动更新内存中数据源

1. 使用的 System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged 模式<xref:System.Windows.Forms.Binding>将控件绑定到数据源的对象。 有两个选项可用于更新数据源：

   - 若要验证控件时更新数据源，请将此属性设置为 System.Windows.Forms.DataSourceUpdateMode.OnValidation。

   - 若要更新的数据源控件的数据绑定属性的值更改时，将此属性设置为 System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged。

     > [!NOTE]
     >  System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged 选项不适用于 Word 主机控件，因为 Word 不提供文档更改或控件更改通知。 但是，此选项可用于 Word 文档中的 Windows 窗体控件。

     下面的示例将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件配置为当该控件中的值更改时自动更新数据源。 此示例假定你有一个名为 <xref:Microsoft.Office.Tools.Excel.NamedRange> 的 `namedRange1` 控件，且其 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 属性已绑定到数据源中的一个字段。

     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>通过使用设计器将控件设置为自动更新内存中数据源

1. 在 Visual Studio 的设计器中，打开 Word 文档或 Excel 工作簿。

2. 单击希望其自动更新数据源的控件。

3. 在“属性”  窗口中，展开“(DataBindings)”  属性。

4. 下一步 **（高级）** 属性中，单击省略号按钮 (![VisualStudioEllipsesButton 屏幕快照](../vsto/media/vbellipsesbutton.png "VisualStudioEllipsesButton 屏幕快照"))。

5. 在“格式设置和高级绑定”  对话框中，单击“数据源更新模式”  下拉列表并选择以下值之一：

    - 若要在验证控件时更新数据源，请选择“OnValidation” 。

    - 若要在控件的数据绑定属性值更改时更新数据源，请选择“OnPropertyChanged” 。

        > [!NOTE]
        >  因为 Word 不提供文档更改或控件更改通知，所以“OnPropertyChanged”  选项不适用于 Word 宿主控件。 但是，此选项可用于 Word 文档中的 Windows 窗体控件。

6. 关闭“格式设置和高级绑定”  对话框。

## <a name="update-the-database"></a>更新数据库
 如果内存中数据源与某个数据库关联，则必须使用对该数据源所做的更改来更新此数据库。 有关更新数据库的详细信息，请参阅[将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)并[使用 TableAdapter 更新数据](../data-tools/update-data-by-using-a-tableadapter.md)。

### <a name="to-update-the-database"></a>更新数据库

1. 调用控件的 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 的 <xref:System.Windows.Forms.BindingSource> 方法。

     在设计时将数据绑定控件添加到文档或工作簿时，会自动生成 <xref:System.Windows.Forms.BindingSource> 。 <xref:System.Windows.Forms.BindingSource> 将该控件连接到项目中的类型化数据集。 有关详细信息，请参阅[BindingSource 组件概述](/dotnet/framework/winforms/controls/bindingsource-component-overview)。

     下面的代码示例假定你的项目包含一个名为 <xref:System.Windows.Forms.BindingSource> 的 `customersBindingSource`。

     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]

2. 调用`Update`在项目中生成的 TableAdapter 的方法。

     在设计时向文档或工作簿添加数据绑定控件时，会自动生成的 TableAdapter。 TableAdapter 将你的项目中的类型化数据集连接到数据库。 有关详细信息，请参阅[TableAdapter 概述](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)。

     下面的代码示例假定 Northwind 数据库中具有与 Customers 表的连接，并且你的项目包含名为 TableAdapter`customersTableAdapter`和一个名为的类型化数据集`northwindDataSet`。

     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]

## <a name="see-also"></a>请参阅
- [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)
- [将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)
- [使用 TableAdapter 更新数据](../data-tools/update-data-by-using-a-tableadapter.md)
- [如何：滚动工作表中的数据库记录](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [如何：用数据库中的数据填充工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [如何：用对象中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [如何：用数据库中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [如何：用服务中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-services.md)
