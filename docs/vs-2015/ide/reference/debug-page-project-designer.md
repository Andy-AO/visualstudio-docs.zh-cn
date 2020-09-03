---
title: “项目设计器”->“调试”页 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 006662d7c07ba0498fff4617eca3fdc7c631d37b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660787"
---
# <a name="debug-page-project-designer"></a>“项目设计器”->“调试”页
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!WARNING]
> 本主题不适用于 Windows 应用商店应用。 请参阅 Windows 开发人员中心的[启动调试会话 (VB, C#, C++ and XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)。

 使用项目设计器的“调试”页为 Visual Basic 或 C# 项目中的调试行为设置属性 。

 要访问“调试”页，请在解决方案资源管理器中选择项目节点 。 在 " **项目** " 菜单上，选择 "项目 _名称_**属性**"。 当项目设计器出现时，请单击“调试”选项卡 。

## <a name="configuration-and-platform"></a>配置和平台
 通过以下选项，可选择要显示或修改的配置和平台。

 **配置**指定要显示或修改的配置设置。 设置可以为“调试”（默认）、“发布”或“所有配置”  。 有关详细信息，请参阅[调试和发布项目配置](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)。

 **平台**指定要显示或修改的平台设置。 这些选择包括“任何 CPU”（默认）、“x64”和“x86”  。 有关详细信息，请参阅[调试和发布项目配置](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)。

## <a name="start-action"></a>启动操作
 "**启动操作**" 指示调试应用程序时要启动的项：项目、自定义程序、URL 或不执行任何操作。 默认情况下，此选项设置为“启动项目”。 “调试”页上的“启动操作”设置确定 `StartAction` 属性的值 。

 **启动项目** 选择此选项可指定调试应用程序时应启动) Windows 应用程序和控制台应用程序项目的可执行文件 (。 默认情况下选择此选项。

 **启动外部程序** 选择此选项可指定调试应用程序时应启动特定程序。

 **启动带有 URL 的浏览器** 选择此选项可指定调试应用程序时应访问特定的 URL。

## <a name="start-options"></a>启动选项
 **命令行参数** 在此文本框中，输入用于调试的命令行参数。

 **工作目录** 在此文本框中，输入将从其启动项目的目录。 或单击“浏览”按钮 (...) 选择目录。

 **使用远程计算机** 若要从远程计算机调试应用程序，请选中此复选框，然后在文本框中输入远程计算机的路径。

## <a name="enable-debuggers"></a>启用调试器
 **启用非托管代码调试** 此选项指定是否支持调试本机代码。 如果正在调用 COM 对象或启动以调用项目的本机代码编写的自定义程序，请选中此复选框并且必须调试此本机代码。 清除此复选框可禁用非托管代码调试。 默认情况下清除此复选框。

 **启用 SQL Server 调试** 选中或清除此复选框可以启用或禁用从您的 Visual Basic 应用程序调试 SQL 过程。 默认情况下清除此复选框。

 **启用 Visual Studio 托管进程** 选中此复选框可启用 Visual Studio 托管进程。 默认情况下，此复选框为选中状态。 有关详细信息，请参阅[托管进程 (vshost.exe)](../../ide/hosting-process-vshost-exe.md)。

 要在安全区域调试，必须启用此选项并在[“高级安全设置”对话框](../../ide/reference/advanced-security-settings-dialog-box.md)中启用“使用所选的权限集调试此应用程序”****。

## <a name="see-also"></a>另请参阅
 [在 Visual Studio 中调试](../../debugger/debugging-in-visual-studio.md) [c # 的项目设置调试](../../debugger/project-settings-for-csharp-debug-configurations.md)[配置 Visual Basic 调试配置的项目设置](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)[管理调试属性](https://msdn.microsoft.com/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)[如何：使用受限权限调试 ClickOnce 应用程序](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)[如何：创建和编辑配置](../../ide/how-to-create-and-edit-configurations.md)
