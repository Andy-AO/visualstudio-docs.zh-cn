---
title: 扩展语言服务以支持 EditorConfig
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be9502569fd57da630da949ba14bbfc5e9045a22
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261817"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>支持 EditorConfig 语言服务

[EditorConfig](http://editorconfig.org/)文件使你可以基于每个项目描述常用的文本编辑器选项，例如缩进大小。 若要了解有关 Visual Studio 支持 EditorConfig 文件的详细信息，请参阅[创建可移植的编辑器设置，请使用 EditorConfig](../ide/create-portable-custom-editor-options.md)。

在大多数情况下，实现 Visual Studio 语言服务时，无需任何其他工作即可支持 EditorConfig 通用属性。 当用户打开文件时，核心编辑器将自动发现并读取 .editorconfig 文件，并设置相应的文本缓冲区和视图选项。 但是，如制表符和空格的编辑，某些语言服务选择使用相应的上下文文本视图选项，而不是无需使用全局设置。 在这些情况下，必须更新语言服务以支持 EditorConfig 文件。

以下是所需更新语言服务以支持 EditorConfig 文件，通过将全局更改_特定于语言_选项与_上下文_选项：

## <a name="indent-style"></a>缩进样式

特定于语言的选项 | 上下文选项
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>缩进大小

特定于语言的选项 | 上下文选项
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>制表符大小

特定于语言的选项 | 上下文选项
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>请参阅

- [创建可移植的编辑器设置，请使用 EditorConfig](../ide/create-portable-custom-editor-options.md)
- [扩展的编辑器和语言服务](../extensibility/extending-the-editor-and-language-services.md)