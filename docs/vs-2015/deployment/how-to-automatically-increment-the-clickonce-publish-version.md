---
title: 如何：自动递增 ClickOnce 发布版本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e82d8019a55af9909b4b623622ac8ff52c565dfb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442191"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>如何：自动递增 ClickOnce 发布版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

发布时[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]应用程序中，更改`Publish Version`属性使此应用程序作为更新发布。 默认情况下，Visual Studio 会自动增大`Revision`数`Publish Version`每次您发布应用程序。  
  
 您可以禁用此行为上**发布**页**项目设计器**。  
  
> [!NOTE]
> 显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅 [在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>若要禁用自动递增发布版本  
  
1. 在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2. 单击“发布”选项卡。  
  
3. 在中**发布版本**部分中，清除**自动递增每个版本的修订号**复选框。  
  
## <a name="see-also"></a>请参阅  
 [如何：设置 ClickOnce 发布版本](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
