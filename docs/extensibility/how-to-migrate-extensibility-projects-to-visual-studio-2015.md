---
title: 如何：将扩展性项目迁移到 Visual Studio 2015 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b7bda175575cf1d48e2f0970bf8202a8041fd16
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072794"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>如何：将扩展性项目迁移到 Visual Studio 2015
下面介绍了如何升级您的扩展插件。

> [!IMPORTANT]
>  如果你想要维护针对早期版本的 Visual Studio 扩展解决方案的版本，请务必在升级之前创建一个副本。 它可能很难返回到其以前的状态的升级后的版本。

### <a name="to-upgrade-an-extensibility-solution"></a>若要升级的可扩展性解决方案

1. 你想要升级，请打开新的版本中使用的副本。 将建议升级是不可逆。

2. 在升级完成后，将外部程序的路径更改为新版本的*devenv.exe*。 右键单击项目节点中的**解决方案资源管理器**，然后选择**属性**。 在中**调试**选项卡上，找到由文本框**启动外部程序**和更改的路径*devenv.exe*到 Visual Studio 2015 路径，其中应如下所示：

     *%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe*

3. 添加对的引用*Microsoft.VisualStudio.Shell.14.0.dll*。 (右键单击项目节点中的**解决方案资源管理器**，然后选择**添加** > **引用**。 选择**扩展**选项卡，然后检查**microsoft.visualstudio.shell.14.0 的引用**。)

4. 生成解决方案。 将生成的文件部署到：

     *%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< 创作名称\>\\< 项目名称\>\\< 项目版本\>\\*。

### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>若要更新到 NuGet VS SDK 引用程序集的可扩展性项目

1. 确定你的项目需要的 VS SDK 引用程序集。  在中**解决方案资源管理器**，展开项目的**引用**节点和检查列表中的项目引用。  VS SDK 的引用程序集将具有前缀**Microsoft.VisualStudio**名称中 (例如：Microsoft.VisualStudio.Shell.14.0).

2. 通过选择它们，右键单击并选择从项目删除 VS SDK 引用程序集**删除**。

3. 添加 VS SDK 引用程序集的 NuGet 的版本。  在仍处于**解决方案资源管理器引用**节点，打开**管理 NuGet 包**对话框。  如果你想要了解有关此对话框的详细信息，请参阅[包管理器 UI](/NuGet/Tools/Package-Manager-UI)。 VS SDK 引用程序集上发布[nuget.org](http://www.nuget.org)通过[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)。

4. 使用**nuget.org**作为你**包源**，搜索 NuGet 包名称相匹配的所需的引用程序集 (例如：Microsoft.visualstudio.shell.14.0 的引用） 并将其安装在项目中。  NuGet 可以添加多个引用程序集，以满足初始程序集的依赖项。

     如果您愿意，您可以通过安装 VS SDK 一次性添加所有 VS SDK 引用程序集[元包](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)。

5. 此外可以切换到使用 VS SDK 生成工具的 NuGet 版本。 此 NuGet 包[Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools)和一次添加到你的项目将包含必要的工具和目标文件，以使您可以在计算机上构建扩展性项目，而无需安装 VS SDK。

> [!NOTE]
>  它不是所需更新现有扩展性项目以使用 NuGet 引用程序集和工具。  他们可以继续使用引用程序集和与 VS SDK 一起安装的工具进行生成。