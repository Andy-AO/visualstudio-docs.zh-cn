---
title: 使用 lambda 表达式或程序块主体
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1f055925a4da916bf88da802e7a4991b0362b057
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789420"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>将表达式主体或程序块主体用于 lambda 表达式

此重构适用于：

- C#

**功能：** 可以重构 lambda 表达式以使用表达式主体或程序块主体。

**使用时机：** 你更倾向于通过 lambda 表达式来使用表达式主体或程序块主体。 

操作原因：可以根据用户偏好重构 Lambda 表达式以提高可读性。

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Lambda 表达式主体或程序块主体重构

1. 请将光标放在 lambda 运算符的右侧。
2. 按“Ctrl”+**。** 触发“快速操作和重构”菜单。

  ![使用 lambda 表达式/程序块主体](media/block-body-lambda.png)

3. 选择“为 lambda 表达式使用程序块主体”或“为 lambda 表达式使用表达式主体”。

## <a name="see-also"></a>请参阅

- [重构](../refactoring-in-visual-studio.md)
- [针对 .NET 开发人员的提示](../../ide/visual-studio-2017-for-dotnet-developers.md)