---
title: 添加显式强制转换
ms.date: 03/26/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e159082266b848ce4742e436c706f3f71b2cc9ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "84182971"
---
# <a name="add-explicit-cast"></a>添加显式强制转换

此代码生成适用于：

- C#

**功能：** 允许根据使用情况，自动向表达式添加显式强制转换。

**使用时机：** 需要向表达式添加显式强制转换，并希望正确地自动分配它。

操作原因：  可以手动向表达式添加显式强制转换，但此功能会根据代码上下文自动添加它。

## <a name="how-to-use-it"></a>使用方法

1. 将脱字号放置在错误上。
2. 按“Ctrl”  + **。** 触发“快速操作和重构”  菜单。
3. 选择“添加显式强制转换”  。

   ![在 Visual Studio 中添加显式强制转换快速操作](media/add-explicit-cast.png)

## <a name="see-also"></a>请参阅

- [代码生成](../code-generation-in-visual-studio.md)
- [重构](../refactoring-in-visual-studio.md)
