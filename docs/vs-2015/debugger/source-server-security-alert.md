---
title: 源服务器安全警报 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f8b122deab5dbdc30b129bce221a804f8c53aa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699327"
---
# <a name="source-server-security-alert"></a>源服务器安全警报
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用源服务器时，只能使用来自已知和受信任位置的符号文件。  
  
 此警告会在你启用源服务器支持时出现。 源服务器命令嵌套在调试符号文件（PDB 文件）中。 请确保你知道自己的 PDB 文件来自何处。  
  
> [!IMPORTANT]
> 使用源服务器时必须考虑以下潜在的安全威胁：任意命令都可嵌入应用程序的 PDB 文件中，因此请确保在 srcsrv.ini 文件中仅放入要执行的命令。 任何尝试执行不在 srcsvr.ini 文件中的命令都将导致出现一个确认对话框。 有关详细信息，请参阅 [安全警告：调试器必须执行不受信任的命令](../debugger/security-warning-debugger-must-execute-untrusted-command.md)。未对命令参数执行任何验证，因此请慎用受信任的命令。 例如，如果你信任 cmd.exe，恶意用户则可能会指定使该命令变得危险的参数。  
  
## <a name="see-also"></a>另请参阅  
 [指定符号 ( .pdb) 文件和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [调试器安全性](../debugger/debugger-security.md)   
 [源服务器](https://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
