---
title: JIT 优化和调试 | Microsoft Docs
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
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 56b010a01ccd7e40e696653e13dd7c972c97a9cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690539"
---
# <a name="jit-optimization-and-debugging"></a>JIT 优化和调试
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

当调试托管应用程序时， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 默认情况下，取消优化实时 (JIT) 代码。 取消 JIT 优化意味着你调试的是非优化代码。 由于代码未优化，因此代码会运行得稍慢一些，但您的调试体验会更全面。 由于调试优化代码要更难一些，因此建议仅在遇到优化代码中发生的 bug 无法在非优化版本中重现时使用。  
  
 JIT 优化在中 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 由 " **在模块加载时取消 jit 优化** " 选项控制。 可以在 "**选项**" 对话框中 "**调试**" 节点下的 "**常规**" 页上找到此选项。  
  
 如果清除 " **在模块加载时取消 JIT 优化** " 选项，则可以调试优化的 JIT 代码，但调试的能力可能会受到限制，因为优化的代码与源代码不匹配。 因此，调试器窗口（如 " **局部变量** **" 和 "** 自动" 窗口）显示的信息可能不会与调试非优化代码时一样多。  
  
 另一个重要差异是有关使用“仅我的代码”进行调试。 如果你正在使用“仅我的代码”进行调试，调试器就会将优化代码作为非用户代码处理，不在调试时显示。 因此，在调试 JIT 优化代码时，您可能想关闭“仅我的代码”。 有关详细信息，请参阅  [限制单步执行到仅我的代码](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code)。  
  
 请记住，当模块加载时，" **在模块加载时取消 JIT 优化** " 选项会取消代码优化。 如果附加到已正在运行的进程，它可能包含已加载的代码、JIT 编译的代码和优化的代码。 " **在模块加载时取消 JIT 优化** " 选项对这些代码无效，尽管它会影响在附加后加载的模块。 此外，" **在模块加载时取消 JIT 优化** " 选项不影响用 NGEN 创建的模块，如 WinForms.dll。  
  
## <a name="see-also"></a>另请参阅  
 [调试托管代码](../debugger/debugging-managed-code.md)   
 [使用调试器在代码中导航](../debugger/navigating-through-code-with-the-debugger.md)   
 [附加到正在运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [托管执行过程](https://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
