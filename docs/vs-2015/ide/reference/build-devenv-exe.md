---
title: -Build (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4c6f5f80512371ae323fbbfe143eb98bffbe7d98
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668361"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用指定解决方案配置文件生成解决方案。  
  
## <a name="syntax"></a>语法  
  
```  
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]  
```  
  
## <a name="arguments"></a>自变量  
 `SolutionName`  
 必需。 解决方案文件的完整路径和名称。  
  
 `SolnConfigName`  
 必需。 `SolutionName` 中指定了将用于生成解决方案的解决方案配置的名称。  
  
 /project `ProjName`  
 可选。 解决方案中项目文件的路径和名称。 可以输入从 `SolutionName` 文件夹到项目文件的相对路径、项目的显示名称或项目文件的完整路径和名称。  
  
 /projectconfig `ProjConfigName`  
 可选。 指定了生成命名的 `/project` 时要使用的项目生成配置的名称。  
  
## <a name="remarks"></a>备注  
 在集成开发环境 (IDE) 中，此开关执行与**生成解决方案**菜单命令相同的功能。  
  
 用双引号将含有空格的字符串引起来。  
  
 “命令”窗口或使用 `/out` 开关指定的任何日志文件中都可显示生成的摘要信息（包括错误）。  
  
 此命令仅生成自上次生成后已更改的项目。 若要生成解决方案中的所有项目，请使用[/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)。  
  
## <a name="example"></a>示例  
 本示例使用 `MySolution` 的 `Debug` 解决方案配置中的 `Debug` 项目生成配置来生成 `CSharpConsoleApp` 项目。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>请参阅  
 [在 Visual Studio 中生成和清理项目和解决方案](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
