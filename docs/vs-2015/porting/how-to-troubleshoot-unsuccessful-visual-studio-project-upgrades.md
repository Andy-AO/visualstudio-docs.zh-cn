---
title: 如何：排查项目升级失败问题 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
f1_keywords:
- VisualStudio.SourceControl.CannotOpenFromSourceControlDSW
- vs.UpgradeProjectSolution.8.0
helpviewer_keywords:
- upgrading applications, Visual Studio
- upgrading projects [Visual Studio]
- projects [Visual Studio], upgrading
- Visual Studio Conversion Wizard
- Conversion wizard
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 31
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 65059e285777e48633da5eb7e8723e3997f37dfa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844441"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>如何：升级 Visual Studio 项目失败疑难解答
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

有时，Visual Studio 不能从早期版本的中完全转换项目 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 如果以下部分中的提示不能解决你的特定问题，则可以在 TechNet [Wiki：开发门户](https://social.technet.microsoft.com/wiki/contents/articles/706.wiki-development-portal.aspx#Visual_Studio)中找到详细信息。

## <a name="the-project-does-not-run-because-files-are-not-found"></a>由于找不到文件，项目不会运行
 在按 F5 时，项目文件包含用于运行项目的硬编码文件路径 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 这些路径可能包括 devenv.exe 和其他所需文件的位置。 在的升级版本中 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，这些文件的路径可能已更改。

#### <a name="to-resolve-incorrect-file-paths"></a>解析错误的文件路径

1. 在文本编辑器中打开项目文件。

2. 扫描可能不正确的文件路径，特别是包含版本号的文件路径 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。

3. 修改不正确的文件路径，使其指向新的目标。

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>该项目不会生成，因为引用无效
 升级时 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，可能也会升级 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本。 如果你的项目包含较新版本中已停用的引用 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ，则可能无法正确解析。 这对于包含版本号的引用特别有用，例如， `Microsoft.VisualStudio.Shell.Interop.8.0` 。

 如果你的代码具有许多无效引用，最简单的解决方案是使用的多目标功能 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 来面向的早期版本 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。

#### <a name="to-resolve-incorrect-references"></a>解析错误引用

1. 在文本编辑器中打开项目文件。

2. 打开项目属性。

3. 选择正确的 " **目标框架** " 值。 另外，还可以 `<TargetFrameworkVersion>` 在项目文件中直接修改元素的值。

   如果希望项目在升级后的版本中运行 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ，则必须更新项目的引用，并更新 `Imports` 调用引用的任何或 `Using` 语句。 如果你的项目在 IDE 中加载，则可以使用 **解决方案资源管理器** 或 " **引用管理器** " 对话框来更新这些引用。

## <a name="see-also"></a>另请参阅
 [/Upgrade ( # A0) ](../ide/reference/upgrade-devenv-exe.md) [转换为 ASP.NET 4](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
