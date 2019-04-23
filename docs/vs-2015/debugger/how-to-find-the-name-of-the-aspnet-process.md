---
title: 如何：查找 ASP.NET 进程的名称 |Microsoft Docs
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
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4cc62b8635a2d7a663b597d4f8a2363fe14ba432
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071923"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>如何：查找 ASP.NET 进程的名称
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要附加到正在运行的 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 应用程序，您必须知道 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 进程的名称：  
  
- 如果正在运行 IIS 6.0 或 IIS 7.0，则名称为 w3wp.exe。  
  
- 如果正在运行 IIS 的早期版本，则该进程的名称为 aspnet_wp.exe。  
  
  通过使用生成的应用程序[!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]或更高版本，[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]代码可以驻留在文件系统上并在测试服务器 WebDev.WebServer.exe 下运行。 在这种情况下，必须附加到 WebDev.WebServer.exe 而不是 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 进程。 此方案仅适用于本地调试。  
  
  当原来的 ASP 应用程序在进程内运行时，它们会在 IIS 进程 inetinfo.exe 内部运行。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅 [在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>确定项目代码驻留在文件系统上还是 IIS 上  
  
1. 在 Visual Studio 中打开**解决方案资源管理器**如果已打开。  
  
2. 选择包含该应用程序名称的顶部节点。  
  
3. 如果**属性**窗口标题包含文件路径，则应用程序代码驻留在文件系统。  
  
     否则为**属性**窗口标题将包含 Web 站点的名称。  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>确定应用程序正在哪个 IIS 版本下运行  
  
1. 查找**管理工具**并运行它。 根据您的操作系统，这可能是中的一个图标**Control Panel**，或当您单击时出现的菜单项**启动**。  
  
     在 Windows XP 中，**控制面板**可以采用分类视图或经典视图。 您需要在类别视图中，单击**切换到经典视图**或**性能和维护**以查看**管理工具**图标。  
  
2. 从**管理工具**，运行 Internet Information Services。 将出现一个 MMC 对话框。  
  
3. 如果左侧窗格中列出了多个计算机，请选择驻留了该应用程序代码的那个计算机。  
  
4. IIS 版本处于**版本**的右窗格中的列。  
  
## <a name="see-also"></a>请参阅  
 [远程调试 Web 应用程序的必备组件](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [系统要求](../debugger/aspnet-debugging-system-requirements.md)   
 [调试 ASP.NET 的准备工作](../debugger/preparing-to-debug-aspnet.md)   
 [调试 Web 应用程序和脚本](../debugger/debugging-web-applications-and-script.md)
