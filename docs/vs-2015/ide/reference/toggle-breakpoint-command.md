---
title: “切换断点”命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 25c9a22db7ae136068ec374f874453dbd4a7c4b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658623"
---
# <a name="toggle-breakpoint-command"></a>“切换断点”命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在文件中的当前位置，根据其当前状态打开或关闭断点。

## <a name="syntax"></a>语法

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>参数
 `text`（可选）。 如果已指定文本，该行将标记为已命名断点。 否则，该行标记为未命名断点，其结果与按下 F9 时的效果类似。

## <a name="example"></a>示例
 以下示例切换当前断点。

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>另请参阅
 [Visual studio](../../ide/reference/visual-studio-commands.md) " [命令" 窗口](../../ide/reference/command-window.md)中的 ["查找/命令" 框](../../ide/find-command-box.md) [visual studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)
