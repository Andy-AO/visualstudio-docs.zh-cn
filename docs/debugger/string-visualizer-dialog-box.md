---
title: 字符串可视化工具对话框 |Microsoft Docs
ms.date: 10/10/2018
ms.custom: seoapril2019
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 982db296fd17fb86b4a139e02a9418eeb507cd91
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59366778"
---
# <a name="string-visualizer-dialog-box"></a>“字符串可视化工具”对话框

在 Visual Studio 中进行调试时，可以使用内置字符串可视化工具查看字符串。 字符串可视化工具显示对于数据提示或调试器窗口而言过长的字符串。 它还可以帮助识别格式错误的字符串。

内置字符串可视化工具包括纯文本、 XML、 HTML 和 JSON 选项。 此外可以打开内置可视化工具的几种其他类型，如[DataSet、 DataTable 和 DataView](../debugger/dataset-visualizer-dialog-box.md)对象，从**自动**或其他调试器窗口。

> [!NOTE]
> 如果您需要检查可视化工具中的 XAML 或 WPF UI 元素，请参阅或[调试时检查 XAML 属性](../debugger/inspect-xaml-properties-while-debugging.md)或[如何使用 WPF 树可视化工具](../debugger/how-to-use-the-wpf-tree-visualizer.md)。

要打开字符串可视化工具，必须在调试期间暂停。 将鼠标悬停在具有纯文本、XML、HTML 或 JSON 字符串值的变量上，然后选择放大镜图标 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "可视化工具图标")。

## <a name="uielement-list"></a>UIElement 列表

**表达式**字段显示的变量或表达式通过将鼠标悬停。

**值**字段显示的字符串值。 空白**值**意味着所选的可视化工具不能识别该字符串。 例如， **XML 可视化工具**显示空白**值**无 XML 标记，一个文本字符串或 JSON 字符串。 若要查看所选的可视化工具无法识别的字符串，请选择**文本可视化工具**相反。 **文本可视化工具**显示纯文本。

### <a name="json-string-data"></a>JSON 字符串数据

格式正确的 JSON 字符串看起来类似于下图中的 JSON 可视化工具。 格式错误的 JSON 可能会显示错误图标（如果无法识别，则为空白）。 若要标识 JSON 错误，请将字符串复制并粘贴到 JSON linting 工具，例如 [JSLint](https://www.jslint.com/)。

![JSON 字符串可视化工具](../debugger/media/dbg-tips-string-visualizer-json.png "JSON 字符串可视化工具")

### <a name="xml-string-data"></a>XML 字符串数据

格式正确的 XML 字符串看起来类似于下图中的 XML 可视化工具。 格式错误的 XML 可能在没有 XML 标记的情况下显示，如果无法识别则显示为空白。

![XML 字符串可视化工具](../debugger/media/dbg-string-visualizers-xml.png "XML 字符串可视化工具")

### <a name="html-string-data"></a>HTML 字符串数据

格式正确的 HTML 字符串的显示方式与在浏览器中的呈现方式相似，如下图所示。 格式错误的 HTML 可能显示为纯文本。

![HTML 字符串可视化工具](../debugger/media/dbg-string-visualizers-html.png "HTML 字符串可视化工具")

## <a name="see-also"></a>请参阅

- [创建自定义可视化工具 （C#、 Visual Basic）](../debugger/create-custom-visualizers-of-data.md)
- [在 Visual Studio for Mac 的数据可视化效果](/visualstudio/mac/data-visualizations)