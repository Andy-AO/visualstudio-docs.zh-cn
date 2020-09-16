---
title: 使用 Visual Basic 开发人员设置管理生成配置
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- advanced build configurations
- building with Visual Basic developer settings (Visual Studio)
- debug builds
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c84978501e5c5bc6f21e8005023c3ae2fe931cce
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038564"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>如何：在应用 Visual Basic 开发人员设置后管理生成配置

默认情况下，应用 Visual Basic 开发人员设置后，所有高级生成配置选项都将隐藏。 本文说明如何手动启用这些生成设置。

## <a name="enable-advanced-build-configurations"></a>启用高级生成配置

默认情况下，Visual Basic 开发人员设置将隐藏用于打开“Configuration Manager”对话框以及[项目设计器](../ide/reference/application-page-project-designer-visual-basic.md)中的“配置”和“平台”列表的选项 。

1. 在 **“工具”** 菜单上，单击 **“选项”** 。

2. 展开“项目和解决方案”并单击“常规”   。

    > [!NOTE]
    > 即使未选中“显示所有设置”选项，“常规”节点也仍然可见   。 如果要查看每个可用选项，请单击“显示所有设置”  。

3. 单击“显示高级生成配置”  。

4. 单击 **“确定”** 。

     现在可在“生成”菜单上使用“Configuration Manager”，并且“项目设计器”上会显示“配置”和“平台”列表      。

## <a name="see-also"></a>请参阅

- [了解生成配置](../ide/understanding-build-configurations.md)
- [编译和生成](../ide/compiling-and-building-in-visual-studio.md)
- [环境设置](../ide/environment-settings.md)
