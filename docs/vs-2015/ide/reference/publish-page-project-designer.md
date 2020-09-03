---
title: “项目设计器”->“发布”页 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
ms.assetid: 153527c6-8b95-4003-8e8e-03a489d0a629
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 391e6c457dd09afa154c46cbc8644f028052cb32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665707"
---
# <a name="publish-page-project-designer"></a>“项目设计器”->“发布”页
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

“项目设计器”  上的“发布”  页面用于针对 ClickOnce 部署配置属性。

 若要访问“发布”  页面，请在“解决方案资源管理器”  中选择项目节点，再在“项目”  菜单上单击“属性”  。 当 **“项目设计器”** 出现时，单击 **“发布”** 选项卡。

> [!NOTE]
> 此处介绍的一些 ClickOnce 属性也可以在“发布向导”（可从“生成”菜单或通过单击此页面上的“发布向导”按钮来使用）中进行设置    。

## <a name="uielement-list"></a>UIElement 列表
 正在**发布文件夹位置**指定发布应用程序的位置。 可以是驱动器路径 (`C:\deploy\myapplication`)、文件共享 (`\\server\myapplication`)、FTP 服务器 (`ftp://ftp.microsoft.com/myapplication`) 或网站 (`http://www.microsoft.com/myapplication`)。 请注意，" **发布位置** " 框中必须存在文本才能使 "浏览 (**...**) " 按钮正常工作。

 默认情况下，如果安装了 IIS，则发布位置为 `http://localhost/<projectname>/` ；如果未安装 IIS，则发布位置为 `publish\` 目录。 如果计算机在运行 Windows Vista，则默认值始终是 `publish\` 目录（无论是否安装了 IIS）。

 **安装文件夹 URL** 可有可无. 指定用户要用于安装应用程序的网站。 仅当与“发布位置”  不同时（例如，将应用程序发布到暂存服务器时），这才是必需的。

 **安装模式和设置**确定应用程序是否直接从**发布位置**运行 (仅当在 **"应用程序处于联机状态**时" 处于选中状态时) 或安装并添加到 "**开始**" 菜单和 "**控制面板**" 中的 "**添加或删除程序**" 项， (当**应用程序脱机可用**时，) 。

 对于 WPF Web 浏览器应用程序，“该应用程序也可以脱机使用” **** 选项处于禁用状态，因为此类应用程序只能联机使用。

 **应用程序文件** 打开 " [应用程序文件" 对话框](https://msdn.microsoft.com/b06dff3a-b87a-4caf-996b-7a4acf8137a8)，该对话框用于指定如何以及在何处安装各个文件。

 **先决条件** 打开 " [系统必备" 对话框](../../ide/reference/prerequisites-dialog-box.md)，该对话框用于指定要与应用程序一起安装的必备组件，如 .NET Framework。

 **更新** 打开 " [应用程序更新" 对话框](https://msdn.microsoft.com/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)，它用于指定应用程序的更新行为。 选择了“该应用程序只能联机使用” **** 时不可用。

 **选项** 打开 " [发布选项" 对话框](https://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592)，该对话框用于指定其他高级发布选项。

 **发布版本** 设置应用程序的发布版本号;版本号发生变化时，应用程序将作为更新发布。 发布版本的每个部分（“主版本”****、“次版本” ****、“生成号” ****、“修订号” ****）的最大值可以是 65355 (<xref:System.UInt16.MaxValue>)，这是 <xref:System.Version>允许的最大值。

 当使用 ClickOnce 安装多个版本的应用程序时，安装会将应用程序的早期版本移动到位于你指定的发布位置的名为“Archive”的文件夹中。 按照这种方式对早期版本进行存档，可以使安装目录与早期版本所在的文件夹分开。

 **每次发布时自动递增修订版本** 可有可无. 选择此选项（默认）时，发布版本号的“修订号” **** 部分会在每次发布应用程序时递增 1。 这将导致应用程序作为更新发布。

 **发布向导** 打开 [发布向导](https://msdn.microsoft.com/fc6abebd-13d6-48e4-a567-fbc52dad0872)。 完成“发布向导”的效果与运行“生成” **** 菜单上的“发布” **** 命令相同。

 **立即发布** 使用当前设置发布应用程序。 等效于“发布向导”中的“完成”按钮********。

## <a name="see-also"></a>另请参阅
 [发布 Clickonce 应用程序](../../deployment/publishing-clickonce-applications.md)[如何：使用发布向导发布 clickonce 应用程序](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)[如何：指定 Visual Studio 复制文件](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)的位置如何：指定[最终用户将从中进行安装的位置](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)如何：指定[用于技术支持的链接](../../deployment/how-to-specify-a-link-for-technical-support.md)[如何：指定 ClickOnce 脱机或联机安装模式](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)[如何：为 CD 安装启用自动启动](../../deployment/how-to-enable-autostart-for-cd-installations.md)[如何：设置 Clickonce 发布版本](../../deployment/how-to-set-the-clickonce-publish-version.md)[如何：自动递增 clickonce 发布版本](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)[如何：](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md) [使用 Clickonce 应用程序安装必备组件](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)[如何：管理](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)clickonce 应用程序的更新如何：为 Clickonce 应用程序[更改发布语言](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)如何：为 Clickonce 应用程序[指定开始菜单名称如何：为 clickonce 应用程序指定开始菜单名称如何：为 clickonce 应用程序指定开始菜单名称](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md) [：指定 ClickOnce 应用程序的发布页](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md) [clickonce 安全和部署](../../deployment/clickonce-security-and-deployment.md)
