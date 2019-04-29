---
title: 选项页的自动化支持 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81cf358d3dfb8fc45a4f696b0483e28673094d44
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62862008"
---
# <a name="automation-support-for-options-pages"></a>选项页的自动化支持
Vspackage 可以提供自定义**选项**到对话框**工具**菜单 (**工具选项**页面) 中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，可以使它们可用于自动化模型。

## <a name="tools-options-pages"></a>工具选项页
 若要创建**工具选项**页上，VSPackage 必须提供返回到 VSPackage 的实现通过环境的用户控件实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法。 (或者，对于托管代码<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法。)

 它是可选的但强烈建议，以允许访问自动化模型通过此新页。 可以通过执行以下步骤进行操作：

1. 扩展<xref:EnvDTE._DTE.Properties%2A>IDispatch 派生的对象实现的对象。

2. 返回的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法 (或托管代码的<xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>方法) 到 IDispatch 派生的对象。

3. 当自动化使用者调用<xref:EnvDTE._DTE.Properties%2A>方法的自定义**选项**属性页中，在环境中使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>方法来获取自定义**工具选项**页面的自动化实现。

4. VSPackage 的自动化对象然后用于提供每个<xref:EnvDTE.Property>返回的<xref:EnvDTE._DTE.Properties%2A>。

   有关示例实现一个自定义**工具选项**页上，请参阅[VSSDK 示例](https://aka.ms/vs2015sdksamples)。

## <a name="see-also"></a>请参阅
- [公开项目对象](../../extensibility/internals/exposing-project-objects.md)