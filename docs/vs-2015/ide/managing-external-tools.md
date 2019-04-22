---
title: 管理外部工具 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1a59432d6b630606ac5c133e8a5811186fcf7c34
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58866754"
---
# <a name="managing-external-tools"></a>管理外部工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以从 Visual Studio 内部调用外部工具。 “工具”菜单上提供了几个默认工具，但你可以添加自己的其他可执行文件。  
  
## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Visual Studio“工具”菜单中提供的工具  
 可从 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中的“工具”菜单调用以下工具。 也可从“快速启动”窗口通过名称调用它们。 例如，若要调用 GuidGen.exe，请键入“创建 GUID”。  
  
1.  创建 GUID：生成 GUID。  
  
2.  错误查找：从输入的值中获取错误消息。 有关详细信息，请参阅 [ERRLOOK 参考](http://msdn.microsoft.com/library/6040ffc1-2355-4a45-8998-84cbcba4ca91)。  
  
3.  ATL/MFC 跟踪工具：显示 ATL 和 MFC 源中的调试跟踪消息。  
  
4.  PreEmptive Protection - Dotfuscator:保护.NET 程序受到反向工程。  
  
5.  SPY + +:以图形方式显示进程、 线程、 窗口和窗口消息。  
  
6.  WCF 服务配置编辑器：可以创建和修改 WCF 服务的配置设置。  
  
> [!WARNING]
>  您可能会看到其他外部工具列表，具体取决于已安装的 Visual Studio 的版本以及已应用的设置配置文件。 有关详细信息，请参阅 [在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## <a name="adding-new-tools"></a>添加新工具  
 可将外部工具添加到“工具”菜单。 打开“外部工具”对话框并单击“添加”，然后填写信息。 例如，以下条目会导致 Windows 资源管理器在当前已在 Visual Studio 中打开的文件目录中打开：  
  
1.  标题:打开文件位置  
  
2.  命令：explorer.exe  
  
3.  参数：/root, "$(ItemDir)"  
  
## <a name="arguments-for-external-tools"></a>外部工具参数  
 以下自变量是在启动外部工具时分配的 Visual Studio 变量。 使用“外部工具”对话框，可以在“工具”菜单上列出指向外部工具（如记事本或 Spy++）的链接。  
  
> [!NOTE]
>  IDE 状态栏会显示当前行和当前列变量，以指示插入点在活动代码编辑器中的位置。 当前文本变量返回在该位置选择的文本或代码。  
  
|名称|参数|描述|  
|----------|--------------|-----------------|  
|项路径|$(ItemPath)|当前文件的完整文件名（驱动器 + 路径 + 文件名）。|  
|项目录|$(ItemDir)|当前文件的目录（驱动器 + 路径）。|  
|项文件名|$(ItemFilename)|当前文件的文件名（文件名）。|  
|项扩展名|$(ItemExt)|当前文件的文件扩展名。|  
|当前行|$(CurLine)|代码窗口中光标的当前行位置。|  
|当前列|$(CurCol)|代码窗口中光标的当前列位置。|  
|当前文本|$(CurText)|选定的文本。|  
|目标路径|$(TargetPath)|要生成的项的完整文件名（驱动器 + 路径 + 文件名）。|  
|目标目录|$(TargetDir)|要生成的项的目录。|  
|Target Name|$(TargetName)|要生成的项的文件名。|  
|目标扩展名|$(TargetExt)|要生成的项的文件扩展名。|  
|二进制目录|$(BinDir)|正在生成的二进制文件的最终位置（定义为驱动器 + 路径）。 例如：**\\...\My Documents\Visual Studio \<Version>\\<ProjectName\>\bin\debug**|  
|项目目录|$(ProjDir)|当前项目的目录（驱动器 + 路径）。|  
|项目文件名|$(ProjFileName)|当前项目的文件名（驱动器 + 路径 + 文件名）。|  
|解决方案目录|$(SolutionDir)|当前解决方案的目录（驱动器 + 路径）。|  
|解决方案文件名|$(SolutionFileName)|当前解决方案的文件名（驱动器 + 路径 + 文件名）。|  
  
## <a name="see-also"></a>请参阅  
 [C/C++ 生成工具](http://msdn.microsoft.com/library/48d9daf4-6bbf-473a-8ce2-bf2923b69f80)
