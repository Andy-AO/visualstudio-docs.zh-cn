---
title: 如何调试 Windows API 函数？ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d7729782fe23c1404aa6862116e884baa97b17f5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103586"
---
# <a name="how-can-i-debug-windows-api-functions"></a>如何调试 Windows API 函数？
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果要调试加载了 NT 符号的 Windows API 函数，必须执行以下步骤。  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>若要在加载了 NT 符号的 Windows API 函数中设置断点  
  
- 输入函数名以及函数所在 DLL 的名称。 在 32 位代码中，使用函数名的修饰形式。 例如，若要给”MessageBeep” 设置断点，你必须输入如下内容。  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     若要获取修饰的名，请参阅[查看修饰名](http://msdn.microsoft.com/f79e2717-a4db-4d12-a689-69830cce2be0)。  
  
## <a name="see-also"></a>请参阅  
 [调试本机代码常见问题](../debugger/debugging-native-code-faqs.md)   
 [调试本机代码](../debugger/debugging-native-code.md)
