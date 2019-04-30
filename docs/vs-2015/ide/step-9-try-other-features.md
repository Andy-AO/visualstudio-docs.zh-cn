---
title: 步骤 9：尝试其他功能 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c8a701715c0adff479fa29dbe9c9b28287031dfd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428289"
---
# <a name="step-9-try-other-features"></a>步骤 9：尝试其他功能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要了解详细信息，请尝试更改图标和颜色、添加游戏计时器和声音。 若要使游戏更具挑战性，请尝试将图板变大并调整计时器。  
  
 若要下载示例的完整版本，请参阅 [Complete Matching Game tutorial sample](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba)（完整匹配游戏教程示例）。  
  
### <a name="to-try-other-features"></a>尝试其他功能  
  
- 将图标和颜色替换为您选择的图标和颜色。  
  
    > [!TIP]
    > 尝试查看标签的 [Forecolor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx) 属性。  
  
- 添加一个游戏计时器，记录玩家赢得游戏所用的时间。  
  
    > [!TIP]
    > 为此，你可以在 TableLayoutPanel 上方的窗体中添加一个标签来显示逝去的时间，并在窗体中添加另一个计时器来记录时间。 使用代码在玩家开始游戏时启动计时器，并在最后两个图标匹配成功后停止计时器。  
  
- 当玩家找到匹配的图标时会添加一种声音，当玩家发现两个不匹配的图标时会添加另一种声音，当程序再次隐藏图标时会添加第三种声音。  
  
    > [!TIP]
    > 若要播放声音，你可以使用 System.media 命名空间。 有关详细信息，请参阅[在 Windows 窗体应用中播放声音 (C# .NET)](http://youtu.be/qOh4ooHg1UU) 或[如何在 Visual Basic 中播放音频](http://youtu.be/-4oPDeQrtMs)。  
  
- 通过将图板变大，增加游戏的难度。  
  
    > [!TIP]
    > 你将不仅需要向 TableLayoutPanel 中添加行和列，还需要考虑创建的图标数目。  
  
- 如果玩家反应太慢，在定量时间前没有选择第二个图标，则隐藏第一个图标，以使游戏更具挑战性。  
  
### <a name="to-continue-or-review"></a>继续或查看  
  
- 如果你遇到困难或在编程方面有疑问，请尝试在一个 MSDN 论坛上发布你的问题。 请参阅 [Visual Basic 论坛](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral)和 [Visual C# 论坛](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral)。  
  
- 那里有很好的免费视频学习资源供你使用。 若要了解有关 Visual Basic 中编程的详细信息，请参阅[Visual Basic 基础知识：零基础开发](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners)。 若要了解有关在视觉对象的编程详细信息C#，请参阅[C#基础知识：零基础开发](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners)。  
  
- 要返回上一个教程步骤，请参阅[步骤 8：添加方法以验证玩家是否获胜](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)。
