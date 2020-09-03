---
title: 属性窗口 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 959bd36995ca4086bf64020816b00aee6f777fbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662073"
---
# <a name="properties-window"></a>“属性”窗口
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用此窗口可查看和更改编辑器和设计器中选中对象的设计时属性和事件。 还可以使用“属性”窗口编辑和查看文件、项目和解决方案属性  。 可以在“视图”菜单上找到“属性”窗口   。 可以按 F4 打开它，也可以在“快速启动”窗口中键入“属性”打开********。

 “属性”窗口显示不同类型的编辑字段，具体取决于特定属性的需要  。 这些编辑字段包括编辑框、下拉列表和自定义编辑器对话框的链接。 以灰色显示的属性为只读属性。

## <a name="uielement-list"></a>UIElement 列表
 对象名称列出当前选定的对象。 只有处于活动状态的编辑器或设计器中的对象是可见的。 选择多个对象时，仅显示所有选定对象的共同属性。

 分类按类别列出所选对象的所有属性和属性值。 可以将类别折叠起来以减少可见属性的数量。 折叠或展开类别时，在类别名称的左侧将显示一个加号 (+) 或减号 (-)。 类别按字母顺序列出。

 按字母顺序对选定对象的所有设计时属性和事件进行排序。 要编辑不灰显的属性，请单击它右侧的单元格并输入更改内容。

 "属性页" 显示选定项的 " **属性页** " 对话框或 " **项目设计器** "。 属性页显示“属性”窗口提供的属性子集、相同属性或属性超集****。 使用此按钮查看和编辑与项目的活动配置相关的属性。

 "属性" 显示对象的属性。 很多对象的事件还可以使用“属性”窗口查看****。

 按属性源组属性按源排序，如继承、应用样式和绑定。 仅在设计器中编辑 XAML 文件时可用。

 事件显示对象的事件。

> [!NOTE]
> 该“属性”窗口工具栏控件仅在 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 项目的上下文中的窗体或控件设计器处于活动状态时可用****。 编辑 XAML 文件时，事件将显示在属性窗口的单独选项卡上。

 消息将列出所有 Windows 消息。 允许针对为选定类提供的消息添加或删除指定处理程序函数。

> [!NOTE]
> 该“属性”窗口工具栏控件仅在“类视图”在 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 项目的上下文中为活动窗口时可用********。

 替代列出了所选类的所有虚函数，并允许您添加或删除重写函数。

> [!NOTE]
> 该“属性”窗口工具栏控件仅在“类视图”在 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 项目的上下文中为活动窗口时可用********。

 说明窗格显示属性类型和属性的简短说明。 可以使用快捷菜单上的说明命令关闭和打开属性的说明。

> [!NOTE]
> 在设计器中编辑 XAML 文件时，此“属性”窗口工具栏控件不可用****。

 缩略图视图在设计器中编辑 XAML 文件时显示当前所选元素的可视表示形式。

 在设计器中编辑 XAML 文件时，搜索为属性和事件提供搜索功能。 搜索框对应于部分单词搜索并在键入时更新搜索结果。

## <a name="see-also"></a>另请参阅
 [项目属性引用](../../ide/reference/project-properties-reference.md)[自定义窗口布局](../../ide/customizing-window-layouts-in-visual-studio.md)
