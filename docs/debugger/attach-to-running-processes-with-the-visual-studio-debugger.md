﻿---
title: 使用 Visual Studio 调试器附加到正在运行的进程 | Microsoft Docs
ms.custom: seodec18
ms.date: 04/08/2019
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
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f810761d088eaf6ec94524a7d76ec255c931686b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60115154"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>使用 Visual Studio 调试器附加到正在运行的进程
可将 Visual Studio 调试器附加到本地或远程计算机上正在运行的进程。 进程运行后，在 Visual Studio 中选择“调试” > “附加到进程”，或按 Ctrl+Alt+P，然后使用“附加到进程”对话框将调试器附加到进程。

可以使用“附加到进程” 来调试本地或远程计算机上正在运行的应用、同时调试多个进程、 调试并非在 Visual Studio 中创建的应用或未使用附带调试器从 Visual Studio 启动的任何应用。 例如，如果运行的是不带调试器的应用，并触发异常，则可以将调试器附加到运行应用的进程并开始调试。

> [!TIP]
> 不确定自己的调试方案是否需要使用“附加到进程”？ 请参阅[常见调试方案](#BKMK_Scenarios)。

## <a name="BKMK_Attach_to_a_running_process"></a> 附加到本地计算机上正在运行的进程

若要快速重新附加到以前附加到进程，请参阅[重新附加到进程](#BKMK_reattach)。

若要调试远程计算机上的进程，请参阅[附加到远程计算机上的进程](#BKMK_Attach_to_a_process_on_a_remote_computer)。

若要附加到本地计算机上的进程，请执行以下操作：

1. 在 Visual Studio 中，选择“调试” > “附加到进程”（或按 Ctrl+Alt+P），打开“附加到进程”对话框。

   “连接类型”应设置为“默认”。 “连接目标”应该是本地计算机名称。

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. 在“可用进程”列表中，查找并选择要附加到的一个或多个进程。

   - 若要快速选择一个进程，请在“筛选进程”框中键入其名称或首字母。

   - 如果不知道进程名称，请浏览列表或参阅[常见调试方案](#BKMK_Scenarios)，了解一些常见的进程名称。

   >[!TIP]
   >“附加到进程”对话框处于打开状态时，进程可以在后台启动和停止，因此正在运行的进程列表可能不总是最新内容。 可随时选择“刷新”查看当前列表。

3. 在“附加到”字段中，确保已列出计划调试的代码类型。 默认的“自动”设置适用于大多数应用类型。

   若要手动选择代码类型：
   1. 单击“选择”。
   1. 在“选择代码类型”对话框中，选择“调试这些代码类型”。
   1. 选择你想要调试的代码类型。
   1. 选择 **确定**。

4. 选择“附加”。

>[!NOTE]
>可附加到多个应用进行调试，但在调试器中一次只能有一个应用处于活动状态。 可在 Visual Studio 的“调试位置”工具栏或“进程”窗口中设置活动的应用。

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>附加到远程计算机上的进程

还可以在“附加到进程”对话框中选择远程计算机，查看该计算机上运行的可用进程列表，并附加到一个或多个进程以进行调试。 远程调试器 (msvsmon.exe) 必须在远程计算机上运行。 有关详细信息，请参阅[远程调试](../debugger/remote-debugging.md)。

用于调试已部署到 IIS 的 ASP.NET 应用程序的更完整说明，请参阅[远程调试远程 IIS 计算机上的 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。

**若要将附加到远程计算机上正在运行的进程：**

1. 在 Visual Studio 中，选择“调试” > “附加到进程”（或按 Ctrl+Alt+P），打开“附加到进程”对话框。

2. 在大多数情况下，“连接类型”应为“默认”。 在“连接目标”框中，使用以下方法之一选择远程计算机：

   - 选择下拉箭头旁边的“连接目标”，并从下拉列表中选择计算机名称。
   - 键入中的计算机名称**连接目标**框，然后按**Enter**。

     验证 Visual Studio 将所需的端口添加到计算机名称，将出现在格式： **\<远程计算机名称 >： 端口**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > 如果您不能使用远程计算机名称进行连接，请尝试使用 IP 和端口地址 (例如， `123.45.678.9:4022`)。 4024 是 Visual Studio 2019 x64 远程调试器的默认端口。 有关其他远程调试器端口分配，请参阅[远程调试器端口分配](remote-debugger-port-assignments.md)。

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > 如果您不能使用远程计算机名称进行连接，请尝试使用 IP 和端口地址 (例如， `123.45.678.9:4022`)。 Visual Studio 2017 x64 远程调试器的默认端口 4022。 有关其他远程调试器端口分配，请参阅[远程调试器端口分配](remote-debugger-port-assignments.md)。

     ::: moniker-end

   - 选择**查找**按钮旁边**连接目标**框，以打开**远程连接**对话框。 **远程连接**对话框会列出本地子网上，或直接连接到您的计算机的所有设备。 你可能需要[打开 UDP 端口 3702](../debugger/remote-debugger-port-assignments.md)服务器以发现远程设备上。 选择的计算机或所需的设备，然后单击**选择**。

   > [!NOTE]
   > “连接类型”设置在调试会话之间保持不变。而“连接目标”设置只有在成功与该目标建立了调试连接时才会在调试会话之间保持不变。

3. 单击“刷新”，填充“可用进程”列表。

    >[!TIP]
    >“附加到进程”对话框处于打开状态时，进程可以在后台启动和停止，因此正在运行的进程列表可能不总是最新内容。 可随时选择“刷新”查看当前列表。

4. 在“可用进程”列表中，查找并选择要附加到的一个或多个进程。

   - 若要快速选择一个进程，请在“筛选进程”框中键入其名称或首字母。

   - 如果不知道进程名称，请浏览列表或参阅[常见调试方案](#BKMK_Scenarios)，了解一些常见的进程名称。

   - 若要查找所有用户帐户下运行的进程，请选择“显示所有用户的进程”复选框。

     >[!NOTE]
     >如果尝试附加到不受信任的用户帐户拥有的进程，则会出现安全警告对话框确认。 有关详细信息请参阅[安全警告：附加到不受信任的用户所拥有的进程可能很危险。以下信息看上去可疑或者你不确定，如果未附加到此进程](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)。

5. 在“附加到”字段中，确保已列出计划调试的代码类型。 默认的“自动”设置适用于大多数应用类型。

   若要手动选择代码类型：
   1. 单击“选择”。
   1. 在“选择代码类型”对话框中，选择“调试这些代码类型”。
   1. 选择你想要调试的代码类型。
   1. 选择 **确定**。

6. 选择“附加”。

>[!NOTE]
>可附加到多个应用进行调试，但在调试器中一次只能有一个应用处于活动状态。 可在 Visual Studio 的“调试位置”工具栏或“进程”窗口中设置活动的应用。

在某些情况下，在远程桌面（终端服务）会话中进行调试时，“可用进程”列表时不会显示所有可用进程。 如果以受限制的用户帐户的用户身份运行 Visual Studio，则“可用进程”列表不会显示在会话 0 中运行的进程。 会话 0 用于服务和其他服务器进程，包括 w3wp.exe。 可通过以下方法解决该问题：使用管理员帐户运行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或从服务器控制台（而不是“终端服务”会话）运行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。

如果这两种解决方法都不可行，第三种方法是通过从 Windows 命令行运行 `vsjitdebugger.exe -p <ProcessId>` 来附加到进程。 您可以确定进程 ID 使用*tlist.exe*。 若要获取“tlist.exe”，请从 [WDK 和 WinDbg 下载](/windows-hardware/drivers/download-the-wdk)中下载并安装适用于 Windows 的调试工具。

## <a name="BKMK_reattach"></a> 重新附加到进程

您可以快速重新附加到先前已通过选择附加到的进程 “调试”  >  “重新附加到进程”(**Shift**+**Alt**+**P**)。 当选择此命令时，调试器会立即尝试附加到最后连接的进程，方法是首次尝试匹配先前的进程 ID ，如果失败，将匹配先前的进程名称。 如果不找到任何匹配项，或多个进程具有相同的名称，“附加到进程” 对话框将打开，这样您就可以选择正确的进程。

> [!NOTE]
> **重新附加到进程**命令是从 Visual Studio 2017 开始，提供。

## <a name="BKMK_Scenarios"></a> 常见的调试方案

为帮助确定是否使用“附加到进程”以及要附加到的进程，下表显示了一些常见调试方案，并提供了指向更多可用说明的链接。 （该列表并未列出详尽信息。）

对于某些应用类型，如通用 Windows 应用 (UWP) ，不能直接附加到进程名称，而需使用 Visual Studio 中的“调试安装的应用程序包”菜单选项（请参阅表格）。

为使调试器附加到用 C++ 编写的代码，该代码需要发出 `DebuggableAttribute`。 可通过链接 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) 链接器选项将它自动添加到代码中。

对于客户端脚本调试，必须在浏览器中启用脚本调试。 对于调试在 Chrome 上的客户端脚本，请选择**Web 工具包**作为代码类型，并根据你的应用类型，可能需要关闭所有 Chrome 实例并在调试模式下启动浏览器 (类型`chrome.exe --remote-debugging-port=9222`从命令行)。

若要快速选择正在运行的进程来将附加到，在 Visual Studio 中，键入**Ctrl**+**Alt**+**P**，然后键入的第一个字母进程名称。

|方案|调试方法|进程名|说明和链接|
|-|-|-|-|
|远程调试 ASP.NET 4 或 4.5 上 IIS 服务器|使用远程工具和**附加到进程**|w3wp.exe|请参阅[远程调试远程 IIS 计算机上的 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS 服务器上的远程调试 ASP.NET Core|使用远程工具和**附加到进程**|*dotnet.exe*|有关应用程序部署，请参阅[发布到 IIS](https://docs.asp.net/en/latest/publishing/iis.html)。 有关调试，请参阅[远程调试远程 IIS 计算机上的 ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|调试客户端脚本的本地 IIS 服务器上，为受支持的应用类型 |使用**附加到进程**|*chrome.exe*， *MicrosoftEdgeCP.exe*，或*iexplore.exe*|必须启用脚本调试。 对于 Chrome 中，也必须在调试模式下，选择运行 Chrome **Webkit 代码**中**附加到**字段。|
|调试C#，Visual Basic 或C++在本地计算机上的应用|使用任一标准调试 (**F5**) 或**附加到进程**|*\<appname>.exe*|在大多数情况下，使用标准调试并不**附加到进程**。|
|远程调试 Windows 桌面应用程序|远程工具|不适用| 请参阅[远程调试C#或 Visual Basic 应用程序](../debugger/remote-debugging-csharp.md)或[远程调试C++应用程序](../debugger/remote-debugging-cpp.md)|
|调试 ASP.NET 应用程序在本地计算机上，在启动不带调试器的应用后|使用**附加到进程**|*iiexpress.exe*|这可能会有所帮助使应用程序加载速度更快，如 （例如） 进行分析时。 |
|调试服务器进程上的其他受支持的应用类型|如果远程服务器，使用远程工具和**附加到进程**|*chrome.exe*， *iexplore.exe*，或其他进程|如有必要，使用资源监视器来帮助标识该进程。 请参阅[远程调试](../debugger/remote-debugging.md)。|
|远程调试的通用 Windows 应用 (UWP)、 OneCore、 HoloLens 或 IoT 应用|调试安装的应用包|不适用|请参阅[调试安装的应用包](debug-installed-app-package.md)而不是使用**附加到进程**|
|调试未从 Visual Studio 启动的通用 Windows 应用 (UWP)、 OneCore、 HoloLens 或 IoT 应用|调试安装的应用包|不适用|请参阅[调试安装的应用包](debug-installed-app-package.md)而不是使用**附加到进程**|

## <a name="use-debugger-features"></a>使用调试器的功能

若要使用的全部功能 （如命中断点） 的 Visual Studio 调试器附加到进程，该应用程序必须完全匹配的本地源和符号。 也就是说，调试器必须能够加载正确[符号 (.pdb) 文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。 默认情况下，这需要调试版本。

对于远程调试方案，必须已在 Visual Studio 中打开了源代码（或源代码的副本）。 远程计算机上编译的应用二进制文件必须与本地计算机上的源自同一版本。

在某些本地调试方案中，如果应用中存在正确的符号文件，则可以在 Visual Studio 中进行调试而无法访问源。 默认情况下，这需要调试版本。 有关详细信息，请参阅[指定符号和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

## <a name="BKMK_Troubleshoot_attach_errors"></a>排查附加错误
 当调试器附加到一个正在运行的进程时，该进程可能包含一种或多种类型的代码。 可在 **“选择代码类型”** 对话框中显示并选择可将调试器附加到的代码类型。

 有时，调试器能够成功附加到一种代码类型，但不能附加到另一种代码类型。 这种情况可能发生在你尝试附加到远程计算机上运行的进程时。 原因是远程计算机上可能安装了一些代码类型的远程调试组件，但没有安装另一些代码类型的远程调试组件。 这种情况还可能发生在你尝试为直接数据库调试附加到两个或多个进程时。 SQL 调试仅支持附加到单个进程。

 如果调试器无法附加到一些，但并非所有代码类型，您将看到消息，指明哪些类型附加操作失败。

 如果调试器成功地附加到至少一种代码类型，你就可以继续调试进程。 你只能调试那些已被成功附加的代码类型。 仍将运行中进程的未附加的代码，但将无法设置断点、 查看数据，或执行其他调试操作对该代码。

 如果要了解有关调试器未能附加到某种代码类型的原因的更具体信息，请尝试重新附加到只为该代码类型。

 **获得有关代码类型未能附加的具体信息：**

1. 从进程中分离。 上**调试**菜单中，选择**全部分离**。

1. 重新附加到进程，仅选择代码类型未能附加。

    1. 在“附加到进程”对话框，选择“可用进程”列表中的进程。

    2. 选择**选择**。

    3. 在 **“选择代码类型”** 对话框中，选择 **“调试以下代码类型”** 和未能附加的代码类型。 取消选择其他代码类型。

    4. 选择 **确定**。

    5. 在中**附加到进程**对话框中，选择**附加**。

    此时，附加将彻底失败，并且你将收到一条特定的错误消息。

## <a name="see-also"></a>请参阅

- [调试多个进程](../debugger/debug-multiple-processes.md)
- [实时调试](../debugger/just-in-time-debugging-in-visual-studio.md)
- [远程调试](../debugger/remote-debugging.md)