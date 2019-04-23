---
title: 如何：查找导致程序崩溃的 DLL |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1da5ba504c22f78ebd3c0705bd5ee903fb4a2997
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060561"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>如何：查找导致程序崩溃的 DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

备注
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在“工具”菜单上选择“导入和导出设置”。 有关详细信息，请参阅 [在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 如果应用程序在调用系统 DLL 或他人的代码时崩溃，则需要找出在崩溃发生时处于活动状态的 DLL。 如果在自己的程序之外的 DLL 中遇到崩溃，则可以使用**模块**窗口识别位置。  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>使用“模块”窗口查找崩溃发生的位置  
  
1. 记下崩溃发生的地址。  
  
2. 在“调试”菜单上，选择“Windows”，然后单击“模块”。  
  
3. 在“模块”窗口中，找到“地址”列。 可能需要使用滚动条来查看。  
  
4. 单击列顶部的“地址”按钮，按地址对 DLL 进行排序。  
  
5. 细查排序的列表，找到其地址包含崩溃位置的 DLL。  
  
6. 查看“名称”和“路径”列来查看 DLL 的名称和路径。  
  
## <a name="see-also"></a>请参阅  
 [如何：调试本机 Dll](../debugger/how-to-debug-native-dlls.md)   
 [如何：使用“模块”窗口](../debugger/how-to-use-the-modules-window.md)
