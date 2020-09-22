---
title: 简化的嵌入 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b8e1ac2fa17409ac3228f87eb71c99ce9e725521
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840350"
---
# <a name="simplified-embedding"></a>简化的嵌入
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果在编辑器的文档视图对象的父级为 (即成为) 的子级，则在编辑器中启用简化嵌入， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 并 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 实现接口以处理其窗口命令。 简化的嵌入编辑器无法承载活动控件。 下图显示了用于创建具有简化嵌入的编辑器的对象。  
  
 ![图：简化的嵌入式编辑器](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
具有简化嵌入的编辑器  
  
> [!NOTE]
> 在此图中的对象中，只 `CYourEditorFactory` 需要对象来创建基于文件的标准编辑器。 如果你正在创建自定义编辑器，则不需要实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> ，因为你的编辑器可能具有自己的专用持久性机制。 但对于非自定义编辑器，必须这样做。  
  
 为创建具有简化嵌入的编辑器而实现的所有接口都包含在 `CYourEditorDocument` 对象中。 但是，若要支持文档数据的多个视图，请将接口拆分为单独的数据并查看对象，如下表所示。  
  
|接口|接口的位置|使用|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|视图|提供与父窗口的连接。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|视图|处理命令。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|视图|启用状态栏更新。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|视图|启用 **工具箱** 项。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|数据|当文件发生更改时发送通知。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|数据|为文件类型启用 "另存为" 功能。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|数据|实现文档持久性。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|数据|允许禁止显示文件更改事件，如重新加载触发。|
