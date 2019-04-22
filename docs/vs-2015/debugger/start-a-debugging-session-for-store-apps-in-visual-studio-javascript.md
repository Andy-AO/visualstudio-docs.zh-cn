---
title: 启动调试会话的应用商店应用 (JavaScript) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5cb08c00679e3052ef0e0715ca58dd010a52e61b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649688"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>在 Visual Studio 中为应用商店应用启动调试会话 (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

适用于 Windows 和 Windows Phone] (../Image/windows_and_phone_content.png"windows_and_phone_content")

 本主题介绍如何针对用 JavaScript 和 HTML5 编写的 Windows 应用商店应用启动调试会话。 你可以使用单个按键启动调试，或者你可以为特定的场景配置调试会话，然后选择启动应用的方式。

> [!NOTE]
>  编写 XAML 和视觉对象中的应用C#、 Visual C++，或 Visual Basic，请参阅[启动调试会话 (VB、 C#，C++和 XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

##  <a name="BKMK_In_this_topic"></a> 在本主题中
 [在本主题中](#BKMK_In_this_topic)

 [启动调试的简单方法](#BKMK_The_easy_way_to_start_debugging)

 [配置调试会话](#BKMK_Configure_the_debugging_session)

- [打开项目的调试属性页](#BKMK_Open_the_debugging_property_page_for_the_project)

- [选择生成配置选项](#BKMK_Choose_the_build_configuration_options)

- [选择部署目标](#BKMK_Choose_the_deployment_target)

- [选择要使用的调试器](#BKMK_Choose_the_debugger_to_use)

- [（可选）推迟启动调试会话中的应用](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [（可选）禁用网络环回](#BKMK__Optional__Disable_network_loopbacks)

  [启动调试会话](#BKMK_Start_the_debugging_session)

- [启动调试 (F5)](#BKMK_Start_debugging__F5_)

- [启动调试 (F5)，但推迟启动应用程序](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [在调试器中启动已安装的应用程序](#BKMK_Start_an_installed_app_in_the_debugger)

  [将调试器附加到正在运行的应用程序](#BKMK_Attach_the_debugger_to_a_running_app_)

- [将应用程序设置为以调试模式运行](#BKMK_Set_the_app_to_run_in_debug_mode)

- [附加调试器](#BKMK_Attach_the_debugger)

##  <a name="BKMK_The_easy_way_to_start_debugging"></a> 启动调试的简单方法
 ![仅适用于 Windows](../debugger/media/windows-only-content.png "windows_only_content")

1. 在 Visual Studio 中打开应用程序解决方案。

2. 如果解决方案同时包含 Windows 应用商店和 Windows Phone 应用商店应用的项目，请确保要调试的项目是启动项目。 在解决方案资源管理器，选择的项目，然后选择**设为启动项目**从上下文菜单。

3. 按 F5。

   ![仅适用于 Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio 生成并启动附有调试器的应用程序。 持续执行至抵达某个断点、手动暂停执行、发生无法处理的异常或应用程序结束为止。 有关详细信息，请参阅[快速入门：调试 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)。

##  <a name="BKMK_Configure_the_debugging_session"></a> 配置调试会话
 由于脚本未编译，不会应用生成配置和平台设置。 如果你正在调试C++或托管的组件，将设置**Configuration**到**调试**，然后选择目标平台从**配置**对话框。

###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> 打开项目的调试属性页

1.  在“解决方案资源管理器”中，选择项目。 在快捷菜单中，选择 **“属性”**。

2.  展开**配置属性**节点，然后选择**调试**

###  <a name="BKMK_Choose_the_build_configuration_options"></a> 选择生成配置选项

1.  从 **“配置”** 列表中，选择 **“调试”** 或 **“(活动)调试”**。

2.  从 **“平台”** 列表中选择要生成的目标平台。 在大多数情况下，**任何 CPU**是最佳选择。

###  <a name="BKMK_Choose_the_deployment_target"></a> 选择部署目标
 可在 Visual Studio 计算机上、本地计算机上的 Visual Studio 模拟器中或远程计算机上部署和调试应用。 选择从目标**要启动的调试器**上列出**调试**项目属性页。

 ![仅适用于 Windows](../debugger/media/windows-only-content.png "windows_only_content")

 对于 Windows 应用商店应用，选择从以下选项之一**目标设备**列表：

|||
|-|-|
|**本地计算机**|在本地计算机上的当前会话中调试应用程序。 请参阅[在本地计算机上的运行 Windows 应用商店应用](../debugger/run-windows-store-apps-on-the-local-machine.md)。|
|**模拟器**|在 Visual Studio 的 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 应用程序模拟器中调试应用程序。 模拟器是一个桌面窗口，在该窗口中可调试本地计算机上未提供的设备功能，如触摸手势和设备旋转。 请参阅[在模拟器中的运行 Windows 应用商店应用](../debugger/run-windows-store-apps-in-the-simulator.md)。|
|**远程计算机**|在通过 Intranet 连接到本地计算机或使用以太网电缆直接连接到本地计算机的设备上调试应用程序。 若要进行远程调试，必须安装 Visual Studio 远程工具，并且远程设备上必须正在运行这些工具。 请参阅[在远程计算机上的运行 Windows 应用商店应用](../debugger/run-windows-store-apps-on-a-remote-machine.md)。|

 如果选择 **“远程计算机”**，则按以下某种方式指定远程计算机的名称或 IP 地址：

- 输入名称或在远程计算机的 IP 地址**计算机名称**框。

- 选择中的向下箭头**计算机名称**框，然后选择**\<定位...> >**。 然后选择从远程计算机**选择远程调试器连接**对话框。

   ![选择远程调试器连接](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  >  “选择远程调试器连接”对话框显示本地子网上的计算机以及通过以太网电缆直接连接到 Visual Studio 计算机的计算机。 若要指定其他计算机，请在 **“计算机名称”** 框中输入名称。

  ![仅适用于 Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  对于 Windows 应用商店手机应用，选择**设备**或从仿真程序之一**目标设备**列表。

###  <a name="BKMK_Choose_the_debugger_to_use"></a> 选择要使用的调试器
 默认情况下，调试器附加到你应用中的 JavaScript 代码。 你可以选择调试应用组件的本机 C++ 和托管代码，而不是 JavaScript 代码。 在应用程序项目的 **“调试”** 属性页上 **“调试器类型”** 列表中指定要调试的代码。

 选择从以下这些调试器之一**调试器类型**列表：

|||
|-|-|
|**仅限脚本**|调试应用程序中的 JavaScript 代码。 忽略托管代码和本机代码。|
|**仅限本机**|调试应用程序中的本机 C/C++ 代码。 忽略托管代码和 JavaScript 代码。|
|**带脚本的本机**|调试应用中的本机 C++ 代码和 JavaScript 代码。|
|**仅限托管**|调试应用程序中的托管代码。 忽略 JavaScript 代码和本机 C/C++ 代码。|
|**混合(托管和本机)**|调试应用程序中的本机 C/C++ 代码和托管代码。 忽略 JavaScript 代码。|

###  <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a> （可选）推迟启动调试会话中的应用
 默认情况下，启动调试后，Visual Studio 将立即启动应用程序。 也可启动调试会话但推迟启动应用程序。 从“开始”菜单或由激活协定启动应用时或者由其他进程或方法启动应用时，将在调试器中启动应用。 你也可以使用延迟的启动在应用未运行时，在应用中调试你希望执行的后台事件。

 指定是否要延迟中应用的启动**启动应用程序**上列出**调试**应用项目属性页。 选择以下某个选项：

-   选择**否**以延迟启动您的应用程序。

-   选择**是**以立即启动该应用程序。

###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> （可选）禁用网络环回
 ![仅适用于 Windows](../debugger/media/windows-only-content.png "windows_only_content")

 为安全起见，不允许以标准方式安装的 Windows 应用商店应用程序对装有它的设备进行网络调用。 默认情况下，Visual Studio 部署功能为所部署的应用程序创建此规则的例外。 通过此例外，在一台计算机上即可测试通信过程。 向 Window 应用商店提交应用程序之前，应在没有例外的情况下测试应用程序。

 若要移除网络环回例外，请选择**否**从**允许网络 Loopback**上列出**调试**属性页。

##  <a name="BKMK_Start_the_debugging_session"></a> 启动调试会话

###  <a name="BKMK_Start_debugging__F5_"></a> 启动调试 (F5)
 当你选择**开始调试**上**调试**菜单 (键盘：F5)，Visual Studio 附加调试器启动的应用程序。 持续执行至抵达某个断点、手动暂停执行、发生无法处理的异常或应用程序结束为止。

###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> 启动调试 (F5)，但推迟启动应用程序
 你可以将应用设置为在调试模式中运行，但通过调试器之外的方法启动应用。 例如，你可能需要调试从“开始”菜单进行的应用程序启动，或在不启动应用程序的情况下调试应用程序中的后台进程。若要延迟应用程序启动，请执行下列操作：

1. 上**调试**页上的应用程序项目属性中，选择**否**从**启动应用程序**列表。

2. 选择**开始调试**上**调试**菜单 (键盘：F5）。

3. 从“开始”菜单、执行协定或由其他过程启动应用程序。

   随后应用程序在调试模式下启动。 持续执行至抵达某个断点、手动暂停执行、发生无法处理的异常或应用程序结束为止。

   . 有关调试后台任务的详细信息，请参阅[触发器挂起、 继续和后台事件的 Windows 应用商店)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)。

##  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> 在调试器中启动已安装的应用程序
 在使用 F5 启动调试时，Visual Studio 会生成并部署应用程序，将应用程序设置为在调试模式中运行，然后启动应用程序。 若要启动设备上已安装的应用程序，请使用“调试安装的应用程序包”对话框。 在需要调试已从 Windows 应用商店安装的应用程序时，或在具有应用程序的源文件但没有针对应用程序的 Visual Studio 项目时，此过程非常有用。 例如，你的自定义生成系统可能不使用 Visual Studio 项目或解决方案。

 应用程序可安装在本地设备上，也可安装在远程设备上。  你可以立即启动应用程序，或将应用程序设置为当其通过其他进程或方法（如从“开始”菜单或通过激活协定）启动时在调试器中运行，也可以将应用程序设置为当需要在未启动应用程序的情况下调试后台进程时在调试模式中运行。 有关详细信息，请参阅[触发器挂起、 继续和后台事件的 Windows 应用商店)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)。

 若要将已安装的应用程序设置为在调试模式中运行，请执行下列操作：

> [!NOTE]
>  在你启动此过程时，应用程序不得运行。

1. 在 **“调试”** 菜单上，选择 **“调试安装的应用程序包”**

2. 请从列表中选择下列选项之一：

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **本地计算机**  |                                                                                                                在本地计算机上的当前会话中调试应用程序。 请参阅[在本地计算机上的运行 Windows 应用商店应用](../debugger/run-windows-store-apps-on-the-local-machine.md)。                                                                                                                 |
   |   **模拟器**    | 在 Visual Studio 的 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 应用程序模拟器中调试应用程序。 模拟器是一个桌面窗口，在该窗口中可调试本地计算机上未提供的设备功能，如触摸手势和设备旋转。 请参阅[在模拟器中的运行 Windows 应用商店应用](../debugger/run-windows-store-apps-in-the-simulator.md)。 |
   | **远程计算机** |                          在通过 Intranet 连接到本地计算机或使用以太网电缆直接连接到本地计算机的设备上调试应用程序。 若要进行远程调试，必须安装 Visual Studio 远程工具，并且远程设备上必须正在运行这些工具。 请参阅[在远程计算机上的运行 Windows 应用商店应用](../debugger/run-windows-store-apps-on-a-remote-machine.md)。                           |

3. 从 **“安装的应用程序包”** 列表中选择应用程序。

4. 从 **“调试此代码类型”** 列表中选择要使用的调试引擎。

5. （可选）。 选择 **“不启动，但在启动时调试代码”** 以在通过其他某种方法启动应用程序时调试应用程序或调试后台进程。

   在单击 **“启动”** 时，应用程序将启动或设置为在调试模式中运行。

##  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> 将调试器附加到正在运行的应用程序
 若要将调试器附加到 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 应用程序，必须使用可调式包管理器将应用程序设置为以调试模式运行。 可调式包管理器与 Visual Studio 远程工具一并安装。

 当需要调试已安装的应用（如从 Windows 应用商店安装的应用）时，将调试器附加到应用很有用。 在拥有应用程序的源文件，但没有应用程序的 Visual Studio 项目时，必须进行附加。 例如，你的自定义生成系统可能不使用 Visual Studio 项目或解决方案。

 附加到应用：

1.  将应用程序设置为以调试模式运行。 必须在应用程序未运行时执行此操作。

2.  启动该应用程序。 可从“开始”菜单、执行协定或通过某些其他方法启动该应用。

3.  将调试器附加到正在运行的应用程序。

###  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> 将应用程序设置为以调试模式运行

1.  在装有该应用程序的设备上安装 Visual Studio 远程工具。 请参阅[安装远程工具](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools)。

2.  在“开始”菜单上，搜索 `Debuggable Package Manager`，然后启动它。

     随后显示 PowerShell 窗口，该窗口针对 AppxDebug cmdlet 进行了正确的配置。

3.  若要能够调试应用程序，必须指定该应用程序的 PackageFullName 标识符。 若要查看包含 PackageFullName 的所有应用程序的列表，请在 PowerShell 提示符下键入 `Get-AppxPackage` 。

4.  在 PowerShell 提示符下，输入 `Enable-AppxDebug` *PackageFullName* ，其中 *PackageFullName* 是应用的 PackageFullName 标识符。

###  <a name="BKMK_Attach_the_debugger"></a> 附加调试器

> [!TIP]
>  JavaScript 应用使用 wwahost.exe 进程的实例运行。 附加到应用时，如果其他 JavaScript 应用正在运行，你将需要了解应用正在运行的 wwahost.exe 的数字进程 ID (PID)。
>
>  处理此情形的最简单方法是关闭所有其他 JavaScript 应用。 否则，你可以在启动应用之前打开 Windows 任务管理器并记下 wwahost.exe 进程的 ID。 当你指定要附加到进程**可用进程**对话框中，该应用的 wwahost.exe 具有不同于你记录的 id。

 若要附加调试器，请执行以下操作：

1. 在 **“调试”** 菜单上选择 **“附加到进程”**。

    出现 **“附加到进程”** 对话框。

2. 若要附加到远程设备上的应用程序，请在 **“限定符”** 框中指定该远程设备。 你可以：

   -   在 **“限定符”** 框中输入名称。

   -   选择中的下箭头**限定符**框，然后从以前已附加到的设备列表中选择该设备。

   -   选择**查找**从本地子网上设备的列表中选择该设备。

3. 在 **“附加到”** 框中指定要调试的代码类型。

    选择 **“选择”** ，然后执行下列操作之一：

   -   选中 **“自动确定要调试的代码类型”**

   -   选中 **“调试以下代码类型”** ，然后从列表中选择一个或多个类型。

4. 在中**可用进程**列表中，选择适当**wwahost.exe**过程。 使用**标题**列来标识您的应用程序。

5. 选择 **“附加”**。

   Visual Studio 将调试器附加到该进程。 持续执行至抵达某个断点、手动暂停执行、发生无法处理的异常或应用程序结束为止。

## <a name="see-also"></a>请参阅
 [控制调试会话 (JavaScript) 中的执行](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)[快速入门：调试 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md) [触发器挂起、 继续和后台事件的 Windows 应用商店)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [在 Visual Studio 中调试应用](../debugger/debug-store-apps-in-visual-studio.md)
