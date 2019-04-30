---
title: 如何：使用 GPU 线程窗口 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dcb55ee2128d237c2be6f57da828ec3c5877cfdd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445084"
---
# <a name="how-to-use-the-gpu-threads-window"></a>如何：使用 GPU 线程窗口
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在“GPU 线程”窗口中，可以检查和使用在要调试的应用程序中的 GPU 上运行的线程。 有关在 GPU 运行的应用程序的详细信息，请参阅[ C++ AMP 概述](http://msdn.microsoft.com/library/9e593b06-6e3c-43e9-8bae-6d89efdd39fc)。  
  
 “GPU 线程”窗口包含一个表，其中，每个行均表示一组在所有列中具有相同值的 GPU 线程。 您可以对列中的项进行排序、重新排序、移除和分组操作。 您可以在“GPU 线程”窗口中标记、取消标记、冻结（禁止显示）和解冻（恢复）线程。 下面的列将显示在“GPU 线程”窗口中：  
  
- 标记列，可在其中标记要特别注意的线程。  
  
- 活动线程列，其中的黄色箭头指示活动线程。 箭头指示执行在调试器中分解的线程。  
  
- “线程计数”列，显示同一位置的线程数。  
  
- “行”列，显示每组线程所在的代码行。  
  
- “地址”列，显示每组线程所在的指令地址。 默认情况下，此列被隐藏。  
  
- “位置”列，表示源代码中的位置。  
  
- “状态”列，显示线程是处于活动、已阻止、未启动还是完成状态。  
  
- “平铺”列，显示行中的线程的平铺索引。  
  
  表的标头显示将显示的平铺和线程。  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>显示“GPU 线程”窗口  
  
1. 在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。  
  
2. 在项目的“属性页”窗口中，在“配置属性”下，选择“调试”。  
  
3. 在“要启动的调试器”列表中，选择“本地 Windows 调试器”。 在“调试器类型”列表中，选择“仅 GPU”。 必须选择此调试器以便在 GPU 上运行的代码的断点处中断。  
  
4. 选择“确定”  按钮。  
  
5. 在 GPU 代码中设置断点。  
  
6. 在菜单栏上，依次选择“调试”、“开始调试”。 等待应用程序到达断点。  
  
7. 在菜单栏上，依次选择“调试”、“Windows”和“GPU 线程”。  
  
### <a name="to-change-to-a-different-active-thread"></a>更改为不同的活动线程  
  
- 双击该列。 （键盘：选择行并选择 enter 键）。  
  
### <a name="to-display-a-particular-tile-and-thread"></a>显示特定平铺和线程  
  
1. 选择“GPU 线程”窗口中的“展开线程切换器”按钮。  
  
2. 在文本框中输入平铺值和线程值。  
  
3. 选择其上带箭头的按钮。  
  
### <a name="to-display-or-hide-a-column"></a>显示或隐藏列  
  
- 打开“GPU 线程”窗口的快捷菜单，选择“列”，然后选择要显示或隐藏的列。  
  
### <a name="to-sort-by-a-column"></a>按列排序  
  
- 选择列标题。  
  
### <a name="to-group-threads"></a>分组线程  
  
- 打开“GPU 线程”窗口的快捷菜单，选择“分组依据”，然后选择显示的列名称之一。 选择“无”以取消对线程的分组。  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>冻结或解冻线程的某个行  
  
- 打开行的快捷菜单，然后选择“冻结”或“解冻”。  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>标记或取消标记线程的某个行  
  
- 选择线程的标记列，或打开线程的快捷菜单并选择“标记”或“取消标记”。  
  
### <a name="to-display-only-flagged-threads"></a>仅显示标记的线程  
  
- 在“GPU 线程”窗口中选择标记按钮。  
  
## <a name="see-also"></a>请参阅  
 [调试多线程应用程序](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何：使用“并行监视”窗口](../debugger/how-to-use-the-parallel-watch-window.md)   
 [演练：调试 C++ AMP 应用程序](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
