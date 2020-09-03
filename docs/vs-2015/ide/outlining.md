---
title: 大纲显示 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
ms.assetid: d1476758-9d35-4d74-b63c-310661932ecd
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 907d075f597799edd582c9f2bae693eac92c0b2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544958"
---
# <a name="outlining"></a>大纲显示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

你可以选择隐藏视图中的某些代码，方法是折叠某个区域的代码，使其显示在加号 (+) 下面。 单击加号可展开折叠的区域。  (或者，你可以按 CTRL + M + M 折叠区域，然后按 CTRL + M + M 再次展开它。 ) 你还可以通过在大纲边距上双击区域中的任意行来折叠大纲显示区域，该区域显示在代码的左侧。 将鼠标悬停在折叠区域时，可以看见折叠区域的内容提示。

 将鼠标悬停在边距上时也会突出显示大纲边距中的区域。 在某些颜色配置中，默认的突出显示颜色可能看起来很模糊。 可以在 " **工具/选项/环境/字体和颜色/可折叠区域**" 中对其进行更改。

 当处理以大纲方式显示的代码时，可以展开要处理的部分，完成后将其折叠，然后移到其他部分。 如果不希望使用大纲显示方式，可以使用**停止大纲显示**命令删除大纲信息，但是不会影响基础代码。

 “编辑”菜单上的“撤消”和“重做”命令会影响这些操作。 **复制**、**剪切**、**粘贴**和拖放操作可保留大纲信息，但是不保留可折叠区域的状态。 例如，如果复制处于折叠状态的区域，那么**粘贴**操作将把复制的文本作为展开的区域进行粘贴。

> [!CAUTION]
> 如果更改大纲显示区域，那么大纲显示可能失效。 例如，删除或“查找和替换”操作可能删除区域的结尾标记。

 以下命令可在 " **编辑"/"大纲** " 子菜单中找到。

|命令|描述|
|-|-|
|隐藏选定内容|（CTRL + M、CTRL + H）- 折叠所选的代码块，此功能通常不可用于大纲显示，例如 `if` 代码块。 若要移除自定义区域，请使用**停止隐藏当前内容**（或使用 CTRL + M、CTRL + U）。 此命令不可用于 Visual Basic。|
|切换大纲显示展开|- 当游标位于嵌套的折叠部分时，反转大纲最内层部分的当前的隐藏或展开状态。|
|切换所有大纲显示|（CTRL + M、CTRL + L）- 将所有区域设置为相同的折叠或展开状态。 如果一些区域为展开状态，一些为折叠状态，那么将展开折叠区域。|
|停止大纲显示|（CTRL + M、CTRL + P）- 删除整个文档的所有大纲信息。|
|停止隐藏当前内容|（CTRL + M、CTRL + U）- 删除当前所选的用户定义的区域的大纲信息。 此命令不可用于 Visual Basic。|
|折叠到定义|（CTRL + M、CTRL + O）- 折叠所有类型的成员。|
|折叠块：\<logical boundary>|(Visual C++) 折叠包含插入点的函数中的一个区域。 例如，如果插入点在一个循环内，则隐藏此循环。|
|全部折叠：\<logical structures>|(Visual C++) 折叠函数内的所有结构。|

 你还可以使用 Visual Studio SDK 定义想要展开或折叠的文本区域。 请参阅[演练：大纲显示](../extensibility/walkthrough-outlining.md)。
