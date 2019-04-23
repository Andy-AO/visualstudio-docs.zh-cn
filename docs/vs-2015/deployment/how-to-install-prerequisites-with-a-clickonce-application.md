---
title: 如何：与 ClickOnce 应用程序一起安装的必备组件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 04f6c78f3733bbc8aab3aec5811f1eb643ecca4e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056609"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>如何：与 ClickOnce 应用程序一起安装必备组件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

所有[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]应用程序要求的计算机上安装.NET Framework 的正确版本之前可运行; 许多应用程序具有其他系统必备组件。 发布时[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]应用程序中，可以选择一组的系统必备组件以与你的应用程序一起打包。 在安装时，检查会执行针对每个必备项，以确定它是否已存在;如果在安装之前将不安装[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]应用程序。  
  
 而不是打包和发布系统必备组件，还可以指定组件的下载位置。 例如，而不是将与每个发布的应用程序的必备组件，您可以使用集中式的文件共享或包含的所有系统必备组件的安装程序的 Web 位置，在安装时，将下载的组件和从该位置安装。  
  
> [!IMPORTANT]
>  应将必备组件安装程序的包添加到开发计算机中，然后发布您的第一个[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]应用程序。 有关详细信息，请参阅[如何：将必备组件与 ClickOnce 应用程序一起添加](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md)。  
  
 在中管理的先决条件**先决条件**对话框中，可通过访问**发布**窗格**项目设计器**。  
  
> [!NOTE]
>  除了预先确定的必备组件列表，可以将您自己的组件添加到列表。 有关详细信息，请参阅[创建引导程序包](../deployment/creating-bootstrapper-packages.md)。  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>若要指定与 ClickOnce 应用程序安装的先决条件  
  
1. 在“解决方案资源管理器” 中选择一个项目，然后在“项目”  菜单上单击“属性” 。  
  
2. 选择**发布**窗格。  
  
3. 单击**先决条件**按钮以打开**先决条件**对话框。  
  
4. 在 **“系统必备”** 对话框中，确保选中 **“创建用于安装系统必备组件的安装程序”** 复选框。  
  
5. 在中**先决条件**列表中，选择的组件，你想要安装，然后依次**确定**。  
  
     所选的组件将打包并随你的应用程序一起发布。  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>若要指定系统必备组件的不同的下载位置  
  
1. 在“解决方案资源管理器” 中选择一个项目，然后在“项目”  菜单上单击“属性” 。  
  
2. 选择**发布**窗格。  
  
3. 单击**先决条件**按钮以打开**先决条件**对话框。  
  
4. 在 **“系统必备”** 对话框中，确保选中 **“创建用于安装系统必备组件的安装程序”** 复选框。  
  
5. 在中**指定系统必备组件的安装位置**部分中，选择**从以下位置下载系统必备组件**。  
  
6. 从下拉列表中，选择一个位置或输入 URL、 文件路径或 FTP 位置，然后单击**确定。**  
  
    > [!NOTE]
    >  必须确保在指定位置中存在的指定组件的安装程序。  
  
## <a name="see-also"></a>请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
