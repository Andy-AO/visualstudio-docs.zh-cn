---
title: “选项”对话框 ->“项目和解决方案”->“VC++ 项目设置”| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 67a35b8987cc9f4f06cc93df2462a4dee326d7e7
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664013"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>“选项”对话框 ->“项目和解决方案”->“VC++ 项目设置”
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用此对话框，可以定义与生成日志和支持文件类型相关的 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 项目设置。  
  
### <a name="to-access-this-dialog-box"></a>访问此对话框  
  
1.  在 **“工具”** 菜单上，单击 **“选项”**。  
  
2.  依次选择“项目和解决方案”和“VC++ 项目设置”。  
  
## <a name="build-customization-search-path"></a>生成自定义搜索路径  
 指定包含 .rules 文件的目录列表，这些文件有助于定义项目的生成规则。  
  
## <a name="build-logging"></a>生成日志  
 **是**  
 启用生成相应的生成日志文件。 此选项可生成位于项目的中间文件目录中的 BuildLog.htm。 每个新的生成文件都会覆盖上一 BuildLog.htm 文件。  
  
 **否**  
 禁用生成相应的生成日志文件。  
  
## <a name="build-timing"></a>生成计时  
 **是**  
 启用生成计时。 如果选中，输出窗口中会发布生成完成所需的时间。 有关详细信息，请参阅[输出窗口](../../ide/reference/output-window.md)。  
  
 **否**  
 禁用生成计时。  
  
## <a name="extensions-to-hide"></a>要隐藏的扩展名  
 指定在“显示所有文件”启用时，不会在“解决方案资源管理器”中显示的文件的文件扩展名。  
  
## <a name="extensions-to-include"></a>要包括的扩展名  
 指定可导入项目的文件的文件扩展名。  
  
## <a name="maximum-concurrent-c-compilations"></a>最大并发 C++ 编译数  
 指定用于并行 C++ 编译的 CPU 内核数目上限。  
  
## <a name="show-environment-in-log"></a>在日志中显示环境  
 **是**  
 在生成日志文件中列出环境变量。 此选项指定在 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 项目生成期间，将所有环境变量回显到生成日志文件中。  
  
 **否**  
 不在生成日志文件中显示环境变量。  
  
## <a name="solution-explorer-mode"></a>解决方案资源管理器模式  
 **仅显示项目中的文件**  
 将“解决方案资源管理器”配置为仅显示项目中的文件。  
  
 **显示所有文件**  
 将“解决方案资源管理器”配置为显示项目中的文件和磁盘上项目文件夹中的文件。  
  
## <a name="see-also"></a>请参阅  
 [生成 C/C++ 程序](http://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008)   
 [C/C++ 生成参考](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)
