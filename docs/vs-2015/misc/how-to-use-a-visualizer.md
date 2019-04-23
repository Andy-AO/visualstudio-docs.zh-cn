---
title: 如何：使用可视化工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0344b9961e7ade31864d70c7d7422f328983abd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60100971"
---
# <a name="how-to-use-a-visualizer"></a>如何：使用可视化工具
您可以使用可视化工具，以对变量或对象的数据类型有意义的方式来显示该变量或对象的内容。 您可以通过使用可视化工具**数据提示**即**监视**窗口中，**自动**窗口中，或**局部变量**窗口。  
  
 Compact Framework 上不支持可视化工具。  
  
> [!NOTE]
>  在中**Store**应用，仅在标准文本支持 HTML、 XML 和 JSON 可视化工具。 不支持自定义（用户创建的）可视化工具。  
  
### <a name="to-open-a-visualizer"></a>打开可视化工具  
  
1. 单击显示中的变量名旁边的放大镜图标**数据提示**即**监视**窗口中，或在**自动**，**局部变量**，或**快速监视**窗口。  
  
     将会显示可视化工具列表。  
  
2. 单击要使用的可视化工具。  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>在远程调试过程中对托管代码使用可视化工具  
  
- 首先将可视化工具 DLL 复制到远程计算机中，然后再启动调试会话。  
  
     远程计算机和本地计算机上的 DLL 路径必须相同。 此路径可为下列任一位置：  
  
     *Visual Studio 安装路径* `\Common7\Packages\Debugger\Visualizers`  
  
     或  
  
     `My Documents\Visual Studio 2010\Visualizers` *Visual Studio 版本* `\Visualizers`  
  
## <a name="see-also"></a>请参阅  
 [创建自定义可视化工具](../debugger/create-custom-visualizers-of-data.md)   
 [如何：安装可视化工具](../debugger/how-to-install-a-visualizer.md)   
 [如何：编写可视化工具](../debugger/how-to-write-a-visualizer.md)   
 [查看数据提示中的数据值](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)