---
title: 使用旧版 API 访问文本视图 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a52ba7fa7e57e63f13cfe502a46d54071ee82591
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313665"
---
# <a name="access-the-text-view-by-using-the-legacy-api"></a>通过使用传统的 API 访问文本视图
文本视图是文本的一个演示文稿的文本缓冲区中存储。 通过使用传统的 API，如以下部分中所示，可以访问在文本视图。

## <a name="text-view-object"></a>文本视图对象
 每个视图程序与自己的文本缓冲区，而视图却是在缓冲区中的数据的窗口。 下图显示了文本视图对象，由表示的密钥接口<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>。

 ![Visual Studio 文本视图对象](../extensibility/media/vstextview.gif)

 视图是显示文本缓冲区中的一种方法。 它包括功能，如自动换行和大纲显示，以便在视图中看到的内容不是精确地表示缓冲区中的文本。

 一个视图，使其他服务或进程可以截获传入命令并查看对它们进行操作之前对其采取措施。 要执行此操作的最常见服务是语言服务。 语言服务可能需要，例如，截获 ENTER 键，以提供自定义缩进的行为或工具提示的命令。

## <a name="add-functionality-to-the-text-view"></a>将功能添加到文本视图
 可以通过处理特定击键自定义文本视图行为。 若要截获击键，则实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>你的对象，并提供命令目标 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) 到监视器和截距命令。

 文本视图命令筛选器的使用顺序体系结构。 新命令筛选器 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>对象) 通过调用添加到序列<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法。

 文本视图的事件通知通过使用提供<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents>接口。 在客户端对象以接收文本视图发生更改的通知上实现此接口。 使用公开此接口到文本视图<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>文本视图以接收更改通知从视图上的接口。

## <a name="see-also"></a>请参阅

- [通过使用传统的 API 更改视图设置](../extensibility/changing-view-settings-by-using-the-legacy-api.md)
- [使用文本管理器来监视全局设置](../extensibility/using-the-text-manager-to-monitor-global-settings.md)