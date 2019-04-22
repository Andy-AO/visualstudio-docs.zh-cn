---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a81c0082bc9b8e31c6c64ff1785f5f380709f3b5
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59650962"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

还原 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 默认设置并自动启动 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE。 可选择将这些设置重置为指定的 .vssettings 文件。  
  
 默认设置由首次启动 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 时选择的配置文件决定。  
  
## <a name="syntax"></a>语法  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>自变量  
 `SettingsFile`  
 .vssettings 文件的完整路径和名称应用于 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
 若要还原常规开发设置配置文件，请使用 `General`。  
  
## <a name="remarks"></a>备注  
 如果未指定任何 `SettingsFile`，在下次启动 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 时，系统将提示选择默认的设置集合。  
  
## <a name="example"></a>示例  
 下面的命令行应用 `MySettings.vssettings` 文件中存储的设置。  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>请参阅  
 [在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)
