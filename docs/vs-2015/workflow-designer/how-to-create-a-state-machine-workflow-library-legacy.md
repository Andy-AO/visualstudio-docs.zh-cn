---
title: 如何：创建状态机工作流库 （旧版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6533ae98e110b3813c6dd7f5520e322ce2cf3496
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433489"
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>如何：创建状态机工作流库（旧版）
按照这些步骤可使用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 提供的旧 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 来创建状态机工作流库项目。 在需要面向 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 时，请使用旧 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。  
  
### <a name="to-create-a-state-machine-workflow-library-project"></a>创建一个状态机工作流库项目  
  
1. 启动 Visual Studio。  
  
2. 在“文件”菜单上，指向“新建”，然后选择“项目”。  
  
     **“新建项目”** 对话框随即打开。  
  
3. 选择任一 **.NET Framework 3.0**选项或 **.NET Framework 3.5**中的下拉列表顶部的选项**新项目**窗口来访问旧设计器。  
  
    > [!NOTE]
    > 中的默认选项[!INCLUDE[vs2010](../includes/vs2010-md.md)]是 **.NET Framework 4**。 此选项用于创建面向 [!INCLUDE[wf](../includes/wf-md.md)] 的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 应用程序，并且不使用旧设计器。  
  
4. 在中**项目类型**窗格中，选择 Visual C# 或 Visual Basic (下**其他语言**)，然后选择**工作流**。  
  
5. 在中**模板**窗格中，选择**状态机工作流库**。  
  
6. 在中**名称**框中，输入您的项目以使其容易识别的描述性名称。  
  
7. 在中**位置**框中，输入想要保存你的项目，或者单击的目录**浏览**以导航到它。  
  
     如果您希望为项目创建一个解决方案目录，选择**创建解决方案目录**复选框并输入中的名称**解决方案名称**框。  
  
8. 单击 **“确定”**。  
  
## <a name="see-also"></a>请参阅  
 [创建旧版工作流项目](../workflow-designer/creating-legacy-workflow-projects.md)   
 [状态机工作流](http://msdn.microsoft.com/library/344caacd-bf3b-4716-bd5a-eca74fc5a61d)