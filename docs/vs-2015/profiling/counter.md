---
title: 计数器 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5da78c33af599accf5ff3a2e09a9afb52982573a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149288"
---
# <a name="counter"></a>计数器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

“计数器”  选项从处理器（硬件）性能计数器收集数据。  
  
- 当使用采样分析方法时，“计数器”  将指定芯片性能计数器和用作采样间隔的计数器事件数。 在使用采样时，仅可以指定一个计数器。  
  
- 当使用检测分析方法时，上一集合事件和当前集合事件间隔内出现的计数器事件数在探查器报表中作为单独字段列出。 使用检测时，可以指定多个“计数器”  选项。  
  
  每个处理器类型都有一组自己的硬件性能计数器。 探查器定义一组几乎所有处理器都通用的泛型性能计数器。 若要列出计算机上的泛型计数器和特定于处理器的计数器，请使用 VSPerfCmd **QueryCounters** 命令。  
  
## <a name="syntax"></a>语法  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]  
```  
  
```  
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]  
```  
  
#### <a name="parameters"></a>参数  
 `Name`  
 计数器的名称。 使用 VSPerfCmd.exe **/QueryCounters** 选项可列出计算机上可用计数器的名称。  
  
 `Reload`  
 采样间隔中的计数器事件数。 不要与检测方法一起使用。  
  
 `FriendlyName`  
 （可选）用于替换探查器报表和视图的列标题中的 `Name` 的字符串。  
  
## <a name="required-options"></a>必需选项  
 “计数器”选项仅可与以下选项之一配合使用：  
  
 **开始时间：**`Trace`  
 初始化探查器以使用检测方法。  
  
 **启动：**`AppName`  
 启动指定的应用程序和探查器。 必须初始化探查器才能使用采样方法。  
  
 **附加：**`PID`  
 启动探查器并将其附加到进程 ID 指定的进程。 必须初始化探查器才能使用采样方法。  
  
## <a name="example"></a>示例  
 采样方法示例演示如何在泛型探查器计数器 NonHaltedCycles 每出现 1000 次时对应用程序进行采样。  
  
 检测方法示例演示如何初始化探查器以便收集 L2InstructionFetches 计数器事件。 L2InstructionFetches 计数器名称特定于处理器。  
  
```  
; Sample Method Example  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"  
  
;INSTRUMENTATION METHOD EXAMPLE  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"  
```  
  
## <a name="see-also"></a>另请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)
