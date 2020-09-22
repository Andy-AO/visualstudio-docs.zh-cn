---
title: 远程调试 ASP.NET 在远程 IIS 7.5 计算机上 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c43f392cddfd5ea36180d9b2675db82469f86ce0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840561"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>远程调试远程 IIS 计算机上的 ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

可以将 ASP.NET Web 应用程序部署到带有 IIS 的 Windows Server 计算机，并将其设置为进行远程调试。 本指南介绍如何设置和配置 Visual Studio 2015 MVC 4.5.2 应用程序、如何将其部署到 IIS 以及如何从 Visual Studio 附加远程调试器。

这些过程已在以下服务器配置上进行了测试：
* Windows Server 2012 R2 和 IIS 10
* Windows Server 2008 R2 和 IIS 7。5

本文中的大多数信息也适用于远程调试 ASP.NET Core 应用程序，只不过 ASP.NET Core 应用的部署不同，需要额外的步骤。 若要将 ASP.NET Core 应用部署到 IIS，需完成 [本文](https://docs.asp.net/en/latest/publishing/iis.html)的所有部分。

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>先决条件：在 Windows Server 计算机上安装远程调试器

有关如何将远程调试器下载到 Windows Server 计算机的说明，请参阅 [远程调试](../debugger/remote-debugging.md)。

若要对 ASP.NET 应用程序进行远程调试，您可以以管理员身份运行远程调试器应用程序，也可以将远程调试器作为服务来启动。 有关如何运行作为一项服务的远程调试器的详细信息，请参阅 [Remote Debugging](../debugger/remote-debugging.md)。

安装后，请确保在目标计算机上运行远程调试器。 如果未 (，请在 "**开始**" 菜单中搜索 "**远程调试器**"。 ) 远程调试器窗口将如下所示。  (4020 是默认端口号) 

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>在 Visual Studio 计算机上创建该应用程序  
  
1. 创建新的 MVC ASP.NET 应用程序。 （“文件”/“新建”/“项目”****，然后选择“Visual C#”/“Web”/“ASP.NET Web 应用程序” **** 。 在 **ASP.NET 4.5.2** 模板部分中，选择“MVC” 。 请确保未在 Azure 部分中选择 " **在云中托管** "。 将项目命名为 **MyMVC**。 ) 
1. 打开 HomeController.cs 文件，并在 `About()` 方法中设置断点。
1. 在“解决方案资源管理器” **** 中，右键单击项目节点并选择“发布” ****。
1. 对于“选择发布目标” ****，选择“自定义” **** 并将该配置文件的命名 **MyMVC**。 单击“下一步”。
1. 在“连接” **** 选项卡上，将“发布方法” **** 字段设置为“文件系统” **** ，并将 **** “目标位置”字段设置为一个本地目录。 单击“下一步”。

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. 设置配置为“调试” ****。 单击“发布”  。

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    应将该应用程序发布到本地目录。

## <a name="deploy-the-aspnet-application-on-the-windows-server-remote-computer"></a><a name="BKMK_deploy_asp_net"></a> 在 Windows Server 远程计算机上部署 ASP.NET 应用程序

 本部分假定 Windows Server 计算机已启用 IIS。 在 Windows Server 2012 R2 上，请参阅 [Iis 配置](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) 以启用 iis。  (您可以跳过本文的其他部分，除非您尝试部署 ASP.NET Core 应用程序。 有关 ASP.NET Core，请按照本文中的步骤部署应用，而不是此处所述的步骤。 ) 
1. 安装 ASP.NET 使用 Web 平台组件从 Windows Server 2012 R2 的服务器节点安装 ASP.NET 4.5 (，选择 " **获取新的 Web 平台组件** "，然后搜索 ASP.NET) 

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    在 Windows Server 2008 R2 上，使用以下命令安装 ASP.NET 4：   **C:\Windows\Microsoft.NET\Framework (64) # A0-ir**
1. 将 ASP.NET 项目目录从 Visual Studio 计算机复制到 Windows Server 计算机上的本地目录（我们命名为 **C:\Publish**）。 可以手动复制项目，使用 Xcopy、Web 部署、Robocopy、Powershell 或其他选项。

    > [!CAUTION]
    > 如果需要更改代码或重新生成，则必须重新发布并重复此步骤。 复制到远程计算机的可执行文件必须与你的本地源和符号完全匹配。
1. 请确保 web.config 文件列出了.NET Framework 的正确版本。  例如，默认情况下，在 Windows Server 2008 R2 上安装 .NET Framework 版本为4.0.30319，但我们创建了 ASP.NET 4.5.2 版本。 如果 ASP.NET 4.0 应用正在 Windows Server 计算机上运行，则需要更改版本：
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```

1. 打开“Internet 信息服务(IIS)管理器”  并转到“站点” 。
1. 右键单击“默认网站”  节点，然后选择“添加应用程序” 。
1. 将 " **别名** " 字段设置为 **MyMVC** ，并将 "应用程序池" 字段设置为 " **ASP.NET** (ASP.NET 4.5 不是应用程序池) 的选项。 将“物理路径” **** 设置为 **C:\Publish** （复制 ASP.NET 项目目录的位置）。

    >[!NOTE] 
    > 对于 ASP.NET Core 应用，请将 "应用程序池" 字段设置为 " **无托管代码**"。
1. 右键单击 " **默认** 网站" 并选择 " **浏览**" 来测试部署。
    如果成功部署了应用，则会显示网页。

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>从 Visual Studio 计算机附加到 ASP.NET 应用程序

1. 在 Visual Studio 计算机上打开 **MyMVC** 解决方案。
1. 在 Visual Studio 中，单击 " **调试"/"附加到进程** " (**Ctrl + Alt + P**) 。
1. 将限定符字段设置为** \<remote computer name> ： 4020**。
1. 单击“刷新”。
    “可用进程”  窗口中将显示某些进程。

    如果看不到任何进程，请尝试使用 IP 地址而不是远程计算机名称（端口是必需的）。 `ipconfig`在命令行中使用来获取 IPv4 地址。
1. 勾选“显示所有用户的进程”  。
1. 查找 **w3wp.exe** 并单击“附加” ****。

     若要快速查找进程名称，请键入进程的第一个字母。
     
    >[!NOTE]
    > 对于 ASP.NET Core 应用，请选择 "dnx.exe" 过程而不是 "w3wp.exe"。  (此过程名称在即将发布的版本中可能会更改。 ) 

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. 打开远程计算机的网站。 在浏览器中，转到 http://\<remote computer name>。
    
    将显示 ASP.NET 网页。
1. 在 ASP.NET 网页中，单击 " **关于** " 页的链接。

    应在 Visual Studio 中命中断点。
