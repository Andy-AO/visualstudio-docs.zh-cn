---
title: 开发 Office 解决方案
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6d4ee308c5c689644c9fd9ca6e85493a081e2cdf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440755"
---
# <a name="develop-office-solutions"></a>开发 Office 解决方案
  使用 Visual Studio 中的 Office 开发人员工具设计项目并设置项目文件后，便可以开始集中精力实现代码和自定义用户界面 (UI)。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

> [!NOTE]
> 开发扩展的 Office 体验跨解决方案是否有兴趣[多个平台](https://dev.office.com/add-in-availability)？ 查看全新[Office 外接程序模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 外接程序具有较小的需求量与 VSTO 外接程序和解决方案，相比，您可以使用几乎任何 web 编程技术，HTML5、 JavaScript、 CSS3 和 XML 等来生成。

## <a name="office-solutions-programming-model"></a>Office 解决方案编程模型
 Office 对象模型公开各种可以编程的对象。 每当使用托管代码进行 Office 解决方案编程，都将编写使用 Office 主互操作程序集中的类型的代码。 在使用 Visual Studio 中的 Office 项目模板创建的解决方案中，还编写直接针对项目中生成的类的代码。 有关详细信息，请参阅[在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)。

## <a name="program-different-types-of-office-solutions"></a>程序不同类型的 Office 解决方案
 你正在创建的解决方案的类型确定你可以在项目中使用的功能。 例如，在设计时通过从 Visual Studio 中的 *“工具箱”* 拖放项，可以向文档级自定义项添加 Windows 窗体控件和扩展的 Office 控件（名为 **主机控件** ）。 但是，如果你正在开发一个 VSTO 外接程序，通过编写代码，可以在运行时仅将这些种类的控件添加到文档。

 有关特定于不同类型解决方案的功能的详细信息，请参阅以下主题：

- [VSTO 外接程序](../vsto/programming-vsto-add-ins.md)。

- [文档级自定义项进行编程](../vsto/programming-document-level-customizations.md)。

- [Office UI 自定义](../vsto/office-ui-customization.md)。

  有关可帮助你规划你的 Office 解决方案和程序以帮助您创建项目的背景信息，请参阅[设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)。

## <a name="related-topics"></a>相关主题

|标题|描述|
|-----------|-----------------|
|[在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)|描述在 Office 解决方案中编写代码的各个方面。|
|[VSTO 外接程序](../vsto/programming-vsto-add-ins.md)|提供对 VSTO 外接程序的编程模型和相关编程任务的概述。|
|[文档级自定义项进行编程](../vsto/programming-document-level-customizations.md)|提供对文档级自定义项的编程模型和相关编程任务的概述。|
|[Office UI 自定义](../vsto/office-ui-customization.md)|介绍可通过使用 VSTO 外接程序和文档级自定义项来自定义 Office 应用程序 UI 的不同方式。|
|[Office 解决方案中的数据](../vsto/data-in-office-solutions.md)|介绍可以使用 Office 解决方案中的数据的不同方法，例如将数据绑定到控件和缓存文档级自定义项中的数据。|
|[自动保存如何影响 Office 解决方案](./how-autosave-impacts-office-solutions.md)|介绍您可能需要启用自动保存时向 Office 解决方案进行的调整。|
|[对 Office 解决方案进行故障排除](../vsto/troubleshooting-office-solutions.md)|提供用于解决在创建 Office 解决方案时可能遇到的常见问题的提示。|
|[Office 中的线程支持](../vsto/threading-support-in-office.md)|提供在 Office 解决方案中使用多个线程的概述。|
|[Office 项目中的辅助功能](../vsto/accessibility-in-office-projects.md)|描述 Office 解决方案中可用的辅助功能。|

## <a name="see-also"></a>请参阅
- [如何：创建和修改自定义文档属性](../vsto/how-to-create-and-modify-custom-document-properties.md)
- [如何：读取和写入到文档属性](../vsto/how-to-read-from-and-write-to-document-properties.md)
- [如何：面向 Office 多语言用户界面](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [演练：为 Excel 创建第一个 VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)
- [演练：创建 excel 在第一个文档级自定义项](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [演练：在第一个 VSTO 外接程序为 Outlook 创建](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)
- [演练：为 PowerPoint 中创建第一个 VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [演练：创建在第一个 VSTO 外接程序项目](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [演练：为 Word 创建第一个 VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)
- [演练：创建 word 在第一个文档级自定义项](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
