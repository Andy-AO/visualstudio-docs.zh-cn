---
title: 适用于 Configuration 和 SelectedItem 对象的自动化 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ee4bcddd7c23f5178984c2c76b059209a965956
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910622"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Configuration 和 SelectedItem 对象的自动化

可以自动生成和 Visual Studio 中的选定的项过程。

## <a name="automation-for-builds"></a>生成自动化

生成或配置已实现时提供的自动化模型<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>。 有关详细信息，请参阅[了解生成配置](../../ide/understanding-build-configurations.md)。

如果你创建 VSPackage，并且想要控制的配置选项，必须使用自动化模型。

## <a name="automation-for-selecteditem"></a>SelectedItem 的自动化

不需要为提供一个实现`SelectedItem`对象，因为 Visual Studio 包含的标准实现。 但是，可以实现`SelectedItem`对象如果您更喜欢。 必须实现一个对象，包含`SelectedItem`接口，并返回到调用的响应<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法替换`VSITEMID`设置为[__VSHPROPID。VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>)。

## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [参与自动化模型](../../extensibility/internals/contributing-to-the-automation-model.md)
- [了解生成配置](../../ide/understanding-build-configurations.md)