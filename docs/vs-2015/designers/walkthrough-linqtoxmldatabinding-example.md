---
title: 演练：LinqToXmlDataBinding 示例 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e97d612e19f64110f3090029dcff82acbad8e87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663975"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>演练：LinqToXmlDataBinding 示例
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本演练介绍 LinqToXmlDataBinding 示例，解释它的两个主要源文件 L2DBForm.xaml 和 L2DBForm.xaml.cs 的一些更值得关注的内容。

## <a name="prerequisites"></a>必备条件
 在阅读本演练之前，强烈建议您生成并运行 LinqToXmlDataBinding 程序，如 [如何：生成和运行 LinqToXmlDataBinding 示例](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)中所述。

## <a name="remarks"></a>备注
 LinqToXmlDataBinding 程序是一个 Windows Presentation Foundation (WPF) 应用程序，由 C# 和 XAML 源文件组成。 它包含定义书籍列表的嵌入式 XML 文档，允许用户查看、添加、删除和编辑这些项。 它由以下两个主要源文件组成：

- L2DBForm.xaml 包含主窗口的用户界面 (UI) 的 XAML 声明代码。 还包含为书籍列表定义数据提供程序和嵌入式 XML 文档的窗口资源部分。

- L2DBForm.xaml.cs 包含与用户界面关联的初始化和事件处理方法。

  主窗口分为以下四个垂直用户界面部分：

- “XML”**** 显示嵌入式书籍列表的原始 XML 源。

- “Book List”（书籍列表）**** 以标准文本形式显示书籍项，允许用户选择和删除各项。

- “Edit Selected Book”（编辑所选书籍）**** 允许用户编辑与当前所选书籍项关联的值。

- “Add New Book”（添加新书籍）**** 允许根据用户输入的值创建新书。

## <a name="in-this-section"></a>本节内容

|主题|说明|
|-----------|-----------------|
|[L2dbform.xaml xaml 源代码](../designers/l2dbform-xaml-source-code.md)|包含文件 L2DBForm.xaml 中的 XAML 代码的内容和描述。|
|[L2DBForm.xaml.cs 源代码](../designers/l2dbform-xaml-cs-source-code.md)|包含文件 L2DBForm.xaml.cs 中的 C# 源代码的内容和描述。|

## <a name="see-also"></a>另请参阅
 [使用 LINQ to XML 示例进行 WPF 数据绑定](../designers/wpf-data-binding-using-linq-to-xml-example.md)[如何：生成和运行 LinqToXmlDataBinding 示例](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)
