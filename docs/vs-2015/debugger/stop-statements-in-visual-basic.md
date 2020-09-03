---
title: Visual Basic 中的 Stop 语句 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f2749ef9a6cfd310da5da832a283b55b6af59a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198888"
---
# <a name="stop-statements-in-visual-basic"></a>Visual Basic 中的 Stop 语句
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Basic Stop 语句提供了一种以编程方式设置断点的替换方法。 当调试器遇到 Stop 语句时，它将中断程序的执行（进入中断模式）。 C# 程序员可通过调用 System.Diagnostics.Debugger.Break 达到同样的效果。  
  
 通过编辑源代码来设置或移除 Stop 语句。 不能使用调试器命令设置或清除 Stop 语句，而对于断点却可以使用调试器命令。  
  
 不同于 End 语句，Stop 语句不重置变量或返回设计模式。 可以从“调试”菜单中选择“继续”继续运行应用程序。  
  
 当在调试器外部运行 Visual Basic 应用程序时，如果启用了实时调试，Stop 语句将启动调试器。 如果没有启用实时调试，Stop 语句的行为如同 End 语句，终止执行。 没有发生 QueryUnload 或 Unload 事件，因此必须从 Visual Basic 应用程序的发布版本中移除所有的 Stop 语句。 有关详细信息，请参阅[实时调试](../debugger/just-in-time-debugging-in-visual-studio.md)。  
  
 若要避免移除 Stop 语句，可以使用条件编译：  
  
```  
#If DEBUG Then  
   Stop  
#Else  
   ' Don't stop  
#End If  
```  
  
 另一种方法是使用 Assert 语句，而不使用 Stop 语句。 Debug.Assert 语句只有在没有满足指定条件时才中断执行，并且当生成发布版本时该语句被自动移除。 有关详细信息，请参阅[托管代码中的断言](../debugger/assertions-in-managed-code.md)。 如果想让 Assert 语句总是在调试版本中中断执行，可以这样做：  
  
```  
Debug.Assert(false)  
```  
  
 还有一种方法是使用 Debug.Fail 方法：  
  
```  
Debug.Fail("a clever output string goes here")  
```  
  
## <a name="see-also"></a>另请参阅  
 [调试器安全性](../debugger/debugger-security.md)   
 [C #、F # 和 Visual Basic 项目类型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [调试托管代码](../debugger/debugging-managed-code.md)
