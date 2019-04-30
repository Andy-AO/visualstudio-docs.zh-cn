---
title: 将附加到正在运行调试器的进程 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- C++
- CSharp
- FSharp
- VB
- c++
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 62
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7e352dcaccd328b4794389726277701014da7be
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436814"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>使用 Visual Studio 调试器附加到运行的进程
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

你可将 Visual Studio 调试器附加到正在本地或远程计算机上运行的进程上。 进程正在运行后，单击**调试 / 附加到进程**(或按**CTRL + ALT + P**) 以打开**附加到进程**对话框。

此功能可用于调试在本地或远程计算机运行的应用程序，同时调试多个进程或调试不在 Visual Studio 中创建的应用程序。 通常很有用时想要调试在应用程序，但 （无论出于什么原因） 您没有启动该应用程序从 Visual Studio 附加调试器。 例如，如果运行不带调试器的应用，并且遇到一个异常，则可能然后附加到运行应用程序以开始调试的进程。

> [!TIP]
> 不确定是否需要使用**附加到进程**为调试方案？ 请参阅[常见调试方案](#BKMK_Scenarios)。 如果你想要调试的 ASP.NET 应用程序部署到 IIS，请参阅[远程 IIS 计算机上的 Remote Debugging ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。

## <a name="BKMK_Attach_to_a_running_process"></a> 将附加到本地计算机上正在运行的进程
 要附加到进程，必须知道进程名称 (请参阅[常见调试方案](#BKMK_Scenarios)的几个常见的进程名称)。

1. 在 Visual Studio 中，选择**调试 / 附加到进程**(或按**CTRL + ALT + P**)。

2. 在 **“附加到进程”** 对话框中的 **“可用进程”** 列表中，找到要附加到的程序。

     若要快速选择所需的进程，请键入进程名称的第一个字母。 如果不知道进程名称，请参阅[常见调试方案](#BKMK_Scenarios)。

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     如果进程在不同的用户帐户下运行，请选中“显示所有用户的进程”复选框。

3. 在“附加到”  对话框中，确保待调试的代码类型已经列出。 默认的 **“自动”** 设置尝试确定要调试的代码类型。 若要手动设置代码类型，请执行以下操作

    1. 在“附加到进程”  对话框中，单击“选择” 。

    2. 在 **“选择代码类型”** 对话框中，单击 **“调试以下代码类型”** ，然后选择要调试的类型。

    3. 单击 **“确定”**。

4. 单击 **“附加”**。

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>附加到远程计算机上的进程
 要附加到进程，必须知道进程名称 (请参阅[常见调试方案](#BKMK_Scenarios)的几个常见的进程名称)。 已部署到 IIS 的 ASP.NET 应用的更完整指南，请参阅[远程 IIS 计算机上的 Remote Debugging ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。 对于其他应用，或许能够在任务管理器中找到进程的名称。

 当使用 **“附加到进程”** 对话框时，你可以选择另一台已经针对远程调试进行设置的计算机。 有关详细信息，请参阅[远程调试](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)。 选择了一台远程计算机后，可以查看该计算机上运行的可用进程的列表，并附加到一个或多个进程以进行调试。

 **若要选择远程计算机：**

1. 在 Visual Studio 中，选择**调试 / 附加到进程**(或按**CTRL + ALT + P**)。

2. 在 **“附加到进程”** 对话框中，从 **“传输”** 列表中选择适当的连接类型。 对于大部分程序来说，**“默认”** 是正确的设置。

   **“传输”** 设置在调试会话之间保持。

3. 使用“限定符”  列表框来通过以下方法之一选择远程计算机名称：

   1. 在 **“限定符”** 列表框中键入名称。

      >**请注意**如果在后续步骤中，不能连接使用远程计算机名称，使用的 IP 地址。 （端口号后，会自动选择相应进程。 您还可以输入其手动。 在下图中，4020 是远程调试器的默认端口。）

   2. 单击附加到 **“限定符”** 列表框的下拉箭头，然后从下拉列表中选择计算机名称。

   3. 单击**查找**按钮旁边**限定符**列表以打开**选择远程调试器连接**对话框。 **“选择远程调试器连接”** 对话框将列出本地子网上的所有设备和通过以太网电缆直接连接到你的计算机的任何设备。 单击所需的计算机或设备，然后单击 **“选择”**。

      **“限定符”** 设置只有相应的限定符发生了成功的调试连接时才会在调试会话之间保持。

4. 单击“刷新”。

     打开 **“进程”** 对话框时，会自动显示 **“可用进程”** 列表。 在该对话框打开时进程可以在后台启动和停止。 不过，内容并非总是最新的。 通过单击 **“刷新”**，可以随时刷新列表以查看当前进程列表。

5. 在 **“附加到进程”** 对话框中的 **“可用进程”** 列表中，找到要附加到的程序。

    如果进程在不同的用户帐户下运行，请选中“显示所有用户的进程”复选框。

6. 单击 **“附加”**。

## <a name="additional-info"></a>其他信息

调试时可以附加到多个程序，但在任何时间，调试器中都只有一个程序处于活动状态。 可以在 **“调试位置”** 工具栏或 **“进程”** 窗口中设置活动程序。 有关详细信息，请参阅[如何：设置当前程序](http://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e)。

如果尝试附加到不受信任的用户帐户拥有的进程，则会出现安全警告对话框确认。 有关详细信息请参阅[安全警告：附加到不受信任的用户所拥有的进程可能很危险。以下信息看上去可疑或者你不确定，如果未附加到此进程](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)。

在某些情况下，在“远程桌面”（“终端服务”）会话中进行调试时， **“可用进程”** 列表不会显示所有可用进程。 如果以具有有限用户帐户的用户身份运行 Visual Studio，“可用进程”  列表将不显示在会话 0 中运行的进程，会话 0 用于服务与其他服务器进程，包括 w3wp.exe。 你可以通过以下方法解决该问题：使用管理员帐户运行 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 或从服务器控制台而不是“终端服务”会话运行 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 如果这两种解决方法都不奏效，第三种方法是通过从 Windows 命令行运行 `vsjitdebugger.exe -p` *ProcessId* 来附加到进程。 你可以使用 tlist.exe 来确定进程 ID。 若要获取 tlist.exe，可从  [WDK 和 WinDbg 下载](http://go.microsoft.com/fwlink/?LinkId=168279)中下载并安装 Windows 调试工具。

## <a name="BKMK_Scenarios"></a> 常见的调试方案

若要帮助你确定是否需要使用**附加到进程**要附加到进程和一些常见的调试方案如下所示 （列表并不详尽）。 其中提供了详细说明，我们提供的链接。

对于某些应用类型 （如 Windows 应用商店应用），不将直接附加到进程名称，但使用**调试安装的应用程序包**菜单选项 （请参见表）。

> [!NOTE]
> 有关在 Visual Studio 基本调试的信息，请参阅[开始使用调试器](../debugger/getting-started-with-the-debugger.md)。

|方案|调试方法|进程名|说明和链接|
|-|-|-|-|
|调试本地计算机上的托管或本机应用|使用附加到进程或[标准调试](../debugger/getting-started-with-the-debugger.md)|*appname*.exe|若要快速访问对话框中，请使用**CTRL + ALT + P** ，然后键入进程名称的第一个字母。|
|在开始使用不带调试器的应用后调试在本地计算机上的 ASP.NET 应用|使用附加到进程|iiexpress.exe|这可能会有所帮助使应用程序加载速度更快，如 （例如） 进行分析时。 |
|远程调试 ASP.NET 4 或 4.5 上 IIS 服务器|使用远程工具和附加到进程|w3wp.exe|请参阅[远程 IIS 计算机上的远程调试 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS 服务器上的远程调试 ASP.NET Core|使用远程工具和附加到进程|dnx.exe|有关应用程序部署，请参阅[发布到 IIS](https://docs.asp.net/en/latest/publishing/iis.html)。 有关调试，请参阅[远程 IIS 计算机上的远程调试 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|调试服务器进程上的其他受支持的应用类型|（如果服务器是远程的），请使用远程工具和附加到进程|iexplore.exe 或其他进程|如有必要，使用任务管理器帮助标识该进程。 请参阅[远程调试](../debugger/remote-debugging.md)和本主题中后面的部分|
|远程调试 Windows 桌面应用程序|远程工具并按 F5|不适用| 请参阅[远程调试](../debugger/remote-debugging.md)|
|远程调试的 Windows 通用 (UWP)、 OneCore、 HoloLens 或 IoT 应用|调试安装的应用包|不适用|使用**调试 / 其他调试目标 / 调试已安装应用程序包**而不是**附加到进程**|
|调试未从 Visual Studio 启动的 Windows 通用 (UWP)、 OneCore、 HoloLens 或 IoT 应用|调试安装的应用包|不适用|使用**调试 / 其他调试目标 / 调试已安装应用程序包**而不是**附加到进程**|

> [!WARNING]
> 若要附加到用 JavaScript 编写的 Windows 通用应用，必须先为该应用启用调试。 请参阅 Windows 开发人员中心中的 [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) 。

> [!NOTE]
> 为使调试器附加到用 C++ 编写的代码，该代码需要发出 `DebuggableAttribute`。 可通过链接 [/ASSEMBLYDEBUG](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) 链接器选项将它自动添加到代码中。

## <a name="what-debugger-features-can-i-use"></a>可以使用哪些调试器功能？

若要使用 Visual Studio 调试器 （如命中断点） 的全部功能的本地源和符号时附加到进程，可执行文件必须完全匹配 (也就是说，调试器必须能够加载正确[符号 (.pbd) 文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). 默认情况下，这需要调试版本。

对于远程调试方案，必须已在 Visual Studio 中打开了源代码（或源代码的副本）。 远程计算机上编译的应用二进制文件必须与本地计算机上的源自同一版本。

某些本地调试的情况下，您可以在 Visual Studio 中使用调试源不能访问正确的符号文件是否存在与该应用程序 （默认情况下，需要调试版本）。 有关详细信息，请参阅[指定符号和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

## <a name="BKMK_Troubleshoot_attach_errors"></a>排查附加错误
 当调试器附加到一个正在运行的进程时，该进程可能包含一种或多种类型的代码。 可在 **“选择代码类型”** 对话框中显示并选择可将调试器附加到的代码类型。

 有时，调试器能够成功附加到一种代码类型，但不能附加到另一种代码类型。 这种情况可能发生在你尝试附加到远程计算机上运行的进程时。 原因是远程计算机上可能安装了一些代码类型的远程调试组件，但没有安装另一些代码类型的远程调试组件。 这种情况还可能发生在你尝试为直接数据库调试附加到两个或多个进程时。 SQL 调试仅支持附加到单个进程。

 如果调试器能够附加到某些代码类型而不是所有代码类型，你将看到一条消息，指示无法附加的类型。

 如果调试器成功地附加到至少一种代码类型，你就可以继续调试进程。 你只能调试那些已被成功附加的代码类型。 上面的示例消息说明未能附加脚本代码类型。 因此，你将不能调试进程内的脚本代码。 进程内的脚本代码将继续运行，但无法设置断点、查看数据或在脚本中执行其他调试操作。

 如果想了解有关调试器未能附加到某种代码类型的详细原因，可以尝试仅重新附加到该代码类型。

 **若要获取有关某种代码类型未能附加的原因的特定信息**

1. 从进程中分离。 在 **“调试”** 菜单上，单击 **“全部分离”**。

2. 再次附加到进程，仅选择单一代码类型。

   1. 在 **“附加到进程”** 对话框的 **“可用进程”** 列表中选择进程。

   2. 单击 **“选择”**。

   3. 在 **“选择代码类型”** 对话框中，选择 **“调试以下代码类型”** 和未能附加的代码类型。 清除任何其他代码。

   4. 单击 **“确定”**。 **“选择代码类型”** 对话框关闭。

   5. 在 **“附加到进程”** 对话框中，单击 **“附加”**。

      此时，附加将彻底失败，并且你将收到一条特定的错误消息。

## <a name="see-also"></a>请参阅
 [调试多个进程](../debugger/debug-multiple-processes.md)[中实时调试](../debugger/just-in-time-debugging-in-visual-studio.md)[远程调试](../debugger/remote-debugging.md)
