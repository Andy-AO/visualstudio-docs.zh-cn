---
title: 调试 64 位应用程序 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d603d2435183581cac92a7c6dae6a4044d8f8fe5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087425"
---
# <a name="debug-64-bit-applications"></a>调试 64 位应用程序
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[调试 64 位应用程序](https://docs.microsoft.com/visualstudio/debugger/debug-64-bit-applications)。  
  
您可以调试运行于本地计算机或远程计算机上的 64 位应用程序。  
  
 若要调试在远程计算机上运行的 64 位应用程序，请参阅[远程调试](../debugger/remote-debugging.md)。  
  
 若要在本地调试 64 位应用程序，Visual Studio 将使用 64 位辅助进程 (msvsmon.exe) 执行不能在 32 位 Visual Studio 进程内执行的低级别操作。  
  
 使用 .NET Framework 3.5 或更早版本的 64 位进程不支持混合模式调试。  
  
## <a name="debug-a-64-bit-application"></a>调试 64 位应用程序  
 若要尝试调试 64 位应用程序：  
  
1. 创建一个 Visual Studio 解决方案，例如 C# 控制台应用程序。  
  
2. 使用配置管理器将配置设置为 64 位。 有关详细信息，请参阅[如何：将项目配置为面向平台](../ide/how-to-configure-projects-to-target-platforms.md)。  
  
3. 此时将启动 64 位版本的远程调试器 (msvsmon.exe)。 只要具有 64 位配置的解决方案处于启用状态，它就会运行。  
  
4. 开始调试。 此体验应该与调试 32 位配置的应用程序的体验相同。 如果出现错误，请参阅下面的“疑难解答”一节。  
  
## <a name="troubleshooting-64-bit-debugging"></a>64 位调试疑难解答  
 可能会看到如下错误："64 位调试操作比预期长。" 在这种情况下，Visual Studio 已向 64 位版本的 msvsmon.exe 发送了一个请求，而返回该请求的结果花费了较长的时间。  
  
 出现此错误的主要原因有两个：  
  
- 你的计算机上所安装的网络安全软件导致网络堆栈不可靠，并且该网络安全软件已删除通过 localhost 的数据包。 请尝试禁用全部的网络安全软件，然后查看该问题是否解决。 如果问题解决，那么请发送报告给你的网络安全软件供应商，说明该软件正在干扰 localhost 通信。  
  
- 你正遇到挂起或 Visual Studio 性能问题。 如果该问题定期发生，你可收集 Visual Studio (devenv.exe) 和辅助进程 (msvsmon.exe) 的转储并将其发送给 Microsoft。 
  
## <a name="see-also"></a>请参阅  
 [64 位应用程序](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [配置 64 位的程序](http://msdn.microsoft.com/library/cb99f72b-8c74-48f4-846a-8921b37b97e9)   
 [Visual Studio IDE 64 位支持](../ide/visual-studio-ide-64-bit-support.md)   
 [使用转储文件](../debugger/using-dump-files.md)   
 [远程调试](../debugger/remote-debugging.md)
