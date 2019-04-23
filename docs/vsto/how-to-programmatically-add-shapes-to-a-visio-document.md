---
title: 如何：以编程方式向 Visio 文档添加形状
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e172ff57fb784d6ae768dde1e705ef645b3f9a9c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117780"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>如何：以编程方式向 Visio 文档添加形状
  可以通过从模具中检索主控形状并将形状放置在活动页面上，向 Microsoft Office Visio 文档添加形状。

 有关详细信息，请参阅 [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) 方法、 [Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) 属性和 [Microsoft.Office.Interop.Visio.Page.Drop](/office/vba/api/Visio.Page.Drop) 方法的 VBA 参考文档。

## <a name="add-shapes-to-a-visio-document"></a>向 Visio 文档添加形状

### <a name="to-add-shapes-to-a-visio-document"></a>若要向 Visio 文档添加形状

- 在文档处于活动状态的情况下，从 Documents.Masters 集合中检索主控形状并将形状放置在活动文档上。 可以使用索引或主控形状名称来检索主控形状。

     下面的代码示例创建一个空白 Visio 文档，然后在“基本形状”  模具停靠的情况下打开它。 该代码随后检索多个形状并将它们放置在活动页面上。

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>请参阅
- [Visio 解决方案](../vsto/visio-solutions.md)
- [Visio 对象模型概述](../vsto/visio-object-model-overview.md)
- [使用 Visio 形状](../vsto/working-with-visio-shapes.md)
- [如何：以编程方式复制和粘贴 Visio 文档中的形状](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)
