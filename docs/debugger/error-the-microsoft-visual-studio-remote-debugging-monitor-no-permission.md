---
title: 错误：远程计算机上的 Microsoft Visual Studio 远程调试监视器没有连接到此计算机的权限
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac6e632927878988f8a3ff86d63fea080a45bd6d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850445"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>错误：远程计算机上的 Microsoft Visual Studio 远程调试监视器没有连接到此计算机的权限

当尝试运行 Visual Studio 远程调试监视器 (msvsmon) 的用户在本地计算机上不具有帐户时，会发生此错误。

## <a name="to-fix-this-problem"></a>修复此问题

- 将一个用户帐户添加到 Visual Studio 调试器主机，该帐户与在远程计算机上运行 msvsmon 的用户帐户具有相同的名称和密码。

   \- 或 -

- 以有权调入本地计算机的用户的身份运行 msvsmon。 这意味着该用户必须是 msvsmon 计算机上的域用户或管理员。 可以指定该用户帐户以两种方式中的任一种来运行 msvsmon：

  - 右击 msvsmon 图标并选择快捷菜单上的“运行方式”

    \- 或 -

  - 在命令提示符处，运行 `runas.exe`。

## <a name="see-also"></a>请参阅

- [远程调试错误和疑难解答](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [远程调试](../debugger/remote-debugging.md)