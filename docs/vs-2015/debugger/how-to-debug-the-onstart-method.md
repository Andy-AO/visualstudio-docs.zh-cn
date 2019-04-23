---
title: 如何：调试 OnStart 方法 |Microsoft Docs
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
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a527a103b72d0026a7732a53b45d03793769058
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078702"
---
# <a name="how-to-debug-the-onstart-method"></a>如何：调试 OnStart 方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

通过启动 Windows 服务并将调试器附加到服务进程，可以调试 Windows 服务。 有关详细信息，请参阅[如何：调试 Windows 服务应用程序](http://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2)。 但是，若要调试 Windows 服务的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> 方法，必须从该方法内部启动调试器。  
  
1. 将对 <xref:System.Diagnostics.Debugger.Launch%2A> 的调用添加到 `OnStart()`方法的开头。  
  
    ```csharp  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2. 启动服务（可以使用 `net start`，或在“服务”  窗口中启动）。  
  
     将显示一个对话框，如下所示：  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3. 选择“是，调试 \<服务名>。”  
  
4. 在“实时调试器”窗口中，选择你想要用于调试的 Visual Studio 版本。  
  
     ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5. 将启动 Visual Studio 新实例，并在 `Debugger.Launch()` 方法处停止执行。  
  
## <a name="see-also"></a>请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [调试托管代码](../debugger/debugging-managed-code.md)
