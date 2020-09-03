---
title: 步骤 9：尝试其他功能 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 379fc9c28b8d36f7bd606719a443b16108f0095d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299972"
---
# <a name="step-9-try-other-features"></a>步骤 9：尝试其他功能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要了解详细信息，请尝试更改图标和颜色、添加游戏计时器和声音。 若要使游戏更具挑战性，请尝试将图板变大并调整计时器。

### <a name="to-try-other-features"></a>尝试其他功能

- 将图标和颜色替换为您选择的图标和颜色。

    > [!TIP]
    > 尝试查看标签的 [Forecolor](https://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx) 属性。

- 添加一个游戏计时器，记录玩家赢得游戏所用的时间。

    > [!TIP]
    > 为此，你可以在 TableLayoutPanel 上方的窗体中添加一个标签来显示逝去的时间，并在窗体中添加另一个计时器来记录时间。 使用代码在玩家开始游戏时启动计时器，并在最后两个图标匹配成功后停止计时器。

- 当玩家找到匹配的图标时会添加一种声音，当玩家发现两个不匹配的图标时会添加另一种声音，当程序再次隐藏图标时会添加第三种声音。

    > [!TIP]
    > 若要播放声音，你可以使用 System.media 命名空间。 有关详细信息，请参阅[在 Windows 窗体应用中播放声音 (C# .NET)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) 或[如何在 Visual Basic 中播放音频](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be)。

- 通过将图板变大，增加游戏的难度。

    > [!TIP]
    > 你将不仅需要向 TableLayoutPanel 中添加行和列，还需要考虑创建的图标数目。

- 如果玩家反应太慢，在定量时间前没有选择第二个图标，则隐藏第一个图标，以使游戏更具挑战性。

### <a name="to-continue-or-review"></a>继续或查看

- 如果你遇到困难或在编程方面有疑问，请尝试在一个 MSDN 论坛上发布你的问题。 请参阅 [Visual Basic 论坛](https://social.msdn.microsoft.com/Forums/en-US/home)和 [Visual C# 论坛](https://social.msdn.microsoft.com/Forums/en-US/home)。

- 那里有很好的免费视频学习资源供你使用。 若要了解有关 Visual Basic 编程的详细信息，请参阅 [Visual Basic Fundamentals: Development for Absolute Beginners](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners)（Visual Basic 基础知识：零基础开发）。 若要了解有关 Visual C# 编程的详细信息，请参阅 [C# Fundamentals: Development for Absolute Beginners](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners)（C# 基础知识：零基础开发）。

- 若要返回到上一个教程步骤，请参阅[步骤 8：添加方法以验证玩家是否获胜](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)。
