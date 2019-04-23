---
title: 调试F#|Microsoft Docs
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
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51a8e43268718421a90d051f0d4d9b6afa96980e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092365"
---
# <a name="debugging-f"></a>调试 F\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

调试 F# 与调试任何托管语言类似，但有以下几种例外情况：

- “自动”窗口不显示 F# 变量。

- F# 不支持“编辑并继续”。 可以在调试会话期间编辑 F# 代码，但应避免这样做。 因为在调试会话期间无法应用代码更改，所以在调试期间编辑 F# 代码将导致源代码和正在调试的代码出现不匹配。

- 调试器无法识别 F# 表达式。 若要在 F# 调试期间在调试器窗口或对话框中输入表达式，必须将该表达式转换为 C# 语法。 在将 F# 表达式转换为 C# 时，请务必记住 C# 使用 == 作为比较运算符中的等号，而 F# 使用单个 =。

## <a name="see-also"></a>请参阅

- [调试托管代码](../debugger/debugging-managed-code.md)
