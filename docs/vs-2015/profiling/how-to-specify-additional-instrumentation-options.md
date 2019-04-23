---
title: 如何：指定其他检测选项 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2440f31b6a6ac345644e20e14b4a82972967fab
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104273"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>如何：指定其他检测选项
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以从 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 集成开发环境 (IDE) 检测二进制文件，或使用命令行工具进行检测。 如果从 IDE 内检测二进制文件，可以在检测期间通过向 [VSInstr](../profiling/vsinstr.md) 工具指定其他检测选项，控制收集的数据量。 这些选项在会话级别或目标级别可用。 例如，若要在检测过程中包括或排除特定函数，请在目标级别使用其他检测选项。  
  
 **要求**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!IMPORTANT]
>  每个插入的探测都将稍微修改原始程序的行为。 此修改将导致分析时产生系统开销。 即使减去此系统开销的近似值，它仍然对多线程应用程序有细微计时影响。 [VSInstr](../profiling/vsinstr.md) 工具选项在分析期间帮助控制数据收集。  
  
### <a name="to-specify-additional-instrumentation-option"></a>指定其他检测选项  
  
1. 在“性能资源管理器”中，选择“性能会话”，然后右键单击并选择“属性”。  
  
2. 在“属性页”中，单击“高级”属性。  
  
3. 在“其他检测选项”框中键入选项。  
  
     例如，使用 /CONTROL:THREAD 指定分析级别。 有关选项的完整列表，请参阅 [VSInstr](../profiling/vsinstr.md)。  
  
4. 单击 **“确定”**。  
  
## <a name="see-also"></a>请参阅  
 [配置性能会话](../profiling/configuring-performance-sessions.md)   
 [从命令行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)
