---
title: 演练：创建边缘字形 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02bc8d858f28799020b958978845c0994accd554
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952798"
---
# <a name="walkthrough-create-a-margin-glyph"></a>演练：创建边缘字形
可以使用自定义编辑器扩展自定义编辑器边距的外观。 本演练中放入自定义标志符号指示器边距时代码注释中显示单词"todo"。

## <a name="prerequisites"></a>系统必备
 从 Visual Studio 2015 开始，不要从下载中心安装 Visual Studio SDK。 它包含作为 Visual Studio 安装程序中的可选功能。 此外可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>创建 MEF 项目

1. 创建一个 C# VSIX 项目。 (在**新的项目**对话框中，选择**Visual C# / 可扩展性**，然后**VSIX 项目**。)将解决方案命名为 `TodoGlyphTest`。

2. 添加编辑器分类器项目项。 有关详细信息，请参阅[使用编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 删除现有的类文件。

## <a name="define-the-glyph"></a>定义标志符号
 通过运行定义标志符号<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>接口。

### <a name="to-define-the-glyph"></a>若要定义标志符号

1. 添加一个类文件并将其命名为 `TodoGlyphFactory`。

2. 通过使用声明中添加以下代码。

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. 添加名为的类`TodoGlyphFactory`实现<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>。

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. 添加定义标志符号尺寸的私有字段。

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. 实现`GenerateGlyph`通过定义标志符号的用户界面 (UI) 元素。 `TodoTag` 稍后在本演练中定义。

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. 添加名为的类`TodoGlyphFactoryProvider`实现<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>。 导出使用此类<xref:Microsoft.VisualStudio.Utilities.NameAttribute>的"TodoGlyph"<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>的后 VsTextMarker<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的"代码"和一个<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>TodoTag。

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. 实现<xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A>方法通过实例化`TodoGlyphFactory`。

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>定义 Todo 标记和标记器
 定义在上一步骤中定义的用户界面元素和指示器边距之间的关系。 创建标记类型和标记器，并将其导出使用标记器提供程序。

### <a name="to-define-a-todo-tag-and-tagger"></a>若要定义 todo 标记和标记器

1. 向项目添加一个新类文件并将其命名`TodoTagger`。

2. 添加以下导入。

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. 添加一个名为类`TodoTag`。

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. 修改名为的类`TodoTagger`，它实现<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>类型的`TodoTag`。

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. 向`TodoTagger`类中，添加私有字段<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>和要查找的分类中的文本的跨度。

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. 添加设置的分类器的构造函数。

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. 实现<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>通过查找所有分类的方法跨其名称中包含单词"注释"，以及其中的文本包括搜索文本。 只要找到搜索文本，重新生成一个新<xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>类型的`TodoTag`。

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. 声明`TagsChanged`事件。

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. 添加名为的类`TodoTaggerProvider`，它实现<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>，并将其与导出<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的"代码"和一个<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>TodoTag。

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. 导入<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>。

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. 实现<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>方法通过实例化`TodoTagger`。

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>生成和测试代码
 若要测试此代码，生成 TodoGlyphTest 解决方案并在实验实例中运行它。

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>若要生成和测试 TodoGlyphTest 解决方案

1. 生成解决方案。

2. 运行该项目通过按**F5**。 Visual Studio 的第二个实例启动。

3. 请确保显示指示器边距。 (在**工具**菜单上，单击**选项**。 在**文本编辑器**页上，请确保**指示器边距**处于选中状态。)

4. 打开具有注释的代码文件。 将单词"todo"添加到注释部分之一。

5. 指示器边距左侧的代码窗口中显示的浅蓝色圆的深蓝色的轮廓。