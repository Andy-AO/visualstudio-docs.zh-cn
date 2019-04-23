---
title: 要添加到设计器的对象使用不同的数据连接与设计器当前正在使用 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 960d3123c45e44b2b1cdc64b896b15b82e655bb2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102831"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>您添加到设计器的对象使用与当前使用的设计器不同的数据连接
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

要添加到设计器中的对象使用的数据连接与设计器当前所用的数据连接不同。 是否要替换设计器使用的连接?  
  
 在将项添加到[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)]（[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]）时，所有项都使用同一个共享数据连接。 （设计图面表示 <xref:System.Data.Linq.DataContext>，它将单个连接用于图面上的所有对象。）如果添加到设计器中的对象使用的数据连接与设计器当前使用的数据连接不同，则会出现此消息。 若要解决此错误，可以选择保持现有连接。 如果选择这样做，则不会添加所选对象。 您也可以选择添加对象并将 <xref:System.Data.Linq.DataContext> 连接重置为新的连接。  
  
> [!NOTE]
>  如果单击**是**，所有实体都类上[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]映射到新的连接。  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>将现有连接替换为所选对象使用的连接  
  
- 单击 **“是”**。  
  
     所选对象将添加到 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]中，并且 DataContext.Connection 设置为新连接。  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>继续使用现有连接并取消添加所选对象的操作  
  
- 单击“否” 。  
  
     操作被取消。 DataContext.Connection 仍然设置为现有连接。  
  
## <a name="see-also"></a>请参阅  
 [LINQ to SQL 工具在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   