---
title: 如何：在应用 Visual Basic 开发人员设置后管理生成配置 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0b0587f6c1c5d7577d8fddffb73db31f09248fae
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075644"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>如何：在应用 Visual Basic 开发人员设置后管理生成配置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

默认情况下，应用 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 开发人员设置后，所有高级生成配置选项都将隐藏。 本主题说明如何手动启用这些设置。  
  
## <a name="enabling-advanced-build-configurations"></a>启用高级生成配置  
 默认情况下，[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 开发人员设置将隐藏用于打开“Configuration Manager”对话框以及[项目设计器中](http://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7)的“配置”和“平台”列表的选项。  
  
#### <a name="to-enable-advanced-build-configurations"></a>启用高级生成配置  
  
1. 在 **“工具”** 菜单上，单击 **“选项”**。  
  
2. 展开“项目和解决方案”并单击“常规”。  
  
    > [!NOTE]
    >  即使未选中“显示所有设置”选项，“常规”节点也仍然可见。 如果要查看每个可用选项，请单击“显示所有设置”。  
  
3. 单击“显示高级生成配置”。  
  
4. 单击 **“确定”**。  
  
     现在可在“生成”菜单上使用“Configuration Manager”，并且“项目设计器”上会显示“配置”和“平台”列表。  
  
## <a name="see-also"></a>请参阅  
 [了解生成配置](../ide/understanding-build-configurations.md)   
 [编译和生成](../ide/compiling-and-building-in-visual-studio.md)
