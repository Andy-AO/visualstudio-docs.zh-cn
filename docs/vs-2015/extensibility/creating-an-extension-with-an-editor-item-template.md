---
title: 使用编辑器项模板创建扩展 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46ccdd87d44ee90c925992f4d7b997c9bbe09684
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840796"
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>使用编辑器项模板创建扩展
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

你可以使用 Visual Studio SDK 中包含的项模板来创建将分类器、修饰和边距添加到编辑器的基本编辑器扩展。 编辑器项模板可用于 Visual c # 或 Visual Basic VSIX 项目。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你不需要从下载中心安装 Visual Studio SDK。 它作为 Visual Studio 安装程序中的可选功能提供。 也可稍后安装 VS SDK。 有关详细信息，请参阅 [安装 Visual STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-classifier-extension"></a>创建分类器扩展  
 编辑器分类器项模板创建一个编辑器分类器，它在此示例中为适当的文本 (颜色，所有内容) 在任何文本文件中。  
  
1. 在 " **新建项目** " 对话框中，展开 " **Visual c #** " 或 " **Visual Basic** "，然后单击 " **扩展性**"。 在 " **模板** " 窗格中选择 " **VSIX 项目**"。 在“名称”  框中键入 `TestClassifier`。 单击“确定”。   
  
2. 在 **解决方案资源管理器**中，右键单击项目节点，然后选择 " **添加/新建项**"。 中转到 "Visual c # **扩展性** " 节点，并选择 " **编辑器分类器**"。 保留默认文件名 (EditorClassifier1.cs) "。  
  
3. 有三个代码文件，如下所示：  
  
    - EditorClassifier1.cs 包含 `EditorClassifier1` 类。  
  
    - EditorClassifier1ClassificationDefinition.cs 包含 `OEditorClassifier1ClassificationDefinition` 类。  
  
    - EditorClassifier1Format.cs 包含 `EditorClassifier1Format`  类。  
  
    - EditorClassifier1Provider.cs 包含 `EditorClassifier1Provider` 类。  
  
4. 生成项目并启动调试。 此时将显示 Visual Studio 的实验实例。  
  
     如果打开文本文件，则所有文本都将以紫色背景为下划线。  
  
## <a name="creating-a-text-relative-adornment-extension"></a>创建文本相关修饰扩展  
 编辑器文本修饰模板创建文本相关修饰，该修饰通过使用具有红色边框和蓝色背景的框来修饰文本字符 "a" 的所有实例。 它是文本相关的，因为方框始终覆盖 "a" 字符，即使它们已被移动或重新格式化也是如此。  
  
1. 在 " **新建项目** " 对话框中，展开 " **Visual c #** " 或 " **Visual Basic** "，然后单击 " **扩展性**"。 在 " **模板** " 窗格中选择 " **VSIX 项目**"。 在“名称”  框中键入 `TestAdornment`。 单击“确定”。   
  
2. 在 **解决方案资源管理器**中，右键单击项目节点，然后选择 " **添加/新建项**"。 中转到 "Visual c # **扩展性** " 节点，然后选择 " **编辑器文本修饰**"。 保留默认文件名 (TextAdornment1.cs/vb) "。  
  
3. 有两个代码文件，如下所示：  
  
    - TextAdornment1.cs 包含 `TextAdornment1` 类。  
  
    - extAdornment1TextViewCreationListener.cs 包含 `TextAdornment1TextViewCreationListener` 类。  
  
4. 生成项目并启动调试。 这将显示实验实例。 如果打开文本文件，文本中的 "a" 字符将以红色显示为蓝色背景。  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>创建视区相关的修饰扩展  
 编辑器视区修饰模板会创建一个视区相关修饰，将具有红色轮廓的紫色框添加到视区的右上角。  
  
> [!NOTE]
> *视区*是当前显示的文本视图区域。  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>使用编辑器视区修饰模板创建视区修饰扩展  
  
1. 在 " **新建项目** " 对话框中，展开 " **Visual c #** " 或 " **Visual Basic** "，然后单击 " **扩展性**"。 在 " **模板** " 窗格中选择 " **VSIX 项目**"。 在“名称”  框中键入 `ViewportAdornment`。 单击“确定”。   
  
2. 在 **解决方案资源管理器**中，右键单击项目节点，然后选择 " **添加/新建项**"。 中转到 "Visual c # **扩展性** " 节点，并选择 " **编辑视区装饰**"。 保留默认文件名 (ViewportAdornment1.cs/vb) "。  
  
3. 有两个代码文件，如下所示：  
  
    - ViewportAdornment1.cs 包含 `ViewportAdornment1` 类。  
  
    - ViewportAdornment1TextViewCreationListener.cs 包含 `ViewportAdornment1TextViewCreationListener` 类  
  
4. 生成项目并启动调试。 这将显示实验实例。 如果创建一个新的文本文件，则会在视区的右上角显示一个具有红色边框的紫罗兰框。  
  
## <a name="creating-a-margin-extension"></a>创建边距扩展  
 编辑器边距模板会创建一个绿色边距，其中显示 "Hello world！" 字样 水平滚动条下方。  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>使用编辑器边距模板创建边距扩展  
  
1. 在 " **新建项目** " 对话框中，展开 " **Visual c #** " 或 " **Visual Basic** "，然后单击 " **扩展性**"。 在 " **模板** " 窗格中选择 " **VSIX 项目**"。 在“名称”  框中键入 `MarginExtension`。 单击“确定”。   
  
2. 在 **解决方案资源管理器**中，右键单击项目节点，然后选择 " **添加/新建项**"。 中转到 "Visual c # **扩展性** " 节点，并选择 " **编辑视区装饰**"。 保留默认文件名 (EditorMargin1.cs/vb) "。  
  
3. 有两个代码文件，如下所示：  
  
    - EditorMargin1.cs 包含 `EditorMargin1` 类。  
  
    - EditorMargin1Factory.cs 包含 `EditorMargin1Factory` 类。  
  
4. 生成此项目并开始调试。 这将显示实验实例。 如果打开一个文本文件，则会在水平滚动条下方显示一个带有单词 "Hello EditorMargin1" 的绿色边距。  
  
## <a name="see-also"></a>另请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)
