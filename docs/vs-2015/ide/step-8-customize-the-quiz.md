---
title: 步骤 8：自定义测验 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 75bde59c6e4b61c2775f188383fc9058a6c31242
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109746"
---
# <a name="step-8-customize-the-quiz"></a>步骤 8：自定义测验
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在本教程的最后一部分中，您将了解一些自定义测验和扩展所学内容的方式。 例如，可考虑程序如何创建一个答案永不为分数的随机除法问题。 若要了解详细信息，请将 `timeLabel` 控件更改为其他颜色，并为测验者提供提示。  
  
### <a name="to-customize-the-quiz"></a>自定义测验  
  
- 通过设置“timeLabel”控件的“BackColor”属性 (`timeLabel.BackColor = Color.Red;`)，使其在测验只剩下 5 秒时变为红色。 当测验结束时重置颜色。  
  
- 当测验参加者在 NumericUpDown 控件中输入正确答案时，通过播放声音来进行提示。 （您必须为每个控件的 `ValueChanged()` 事件编写事件处理程序，只要用户更改控件的值，就激发该事件。）  
  
### <a name="to-continue-or-review"></a>继续或查看  
  
- 若要下载测验的完整版本，请参阅 [Complete Math Quiz tutorial sample](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c)（数学测验教程的完整示例）。  
  
- 要转到下一个教程，请参阅[教程 3：创建匹配游戏](../ide/tutorial-3-create-a-matching-game.md)。  
  
- 要返回上一个教程步骤，请参阅[步骤 7：添加乘法和除法问题](../ide/step-7-add-multiplication-and-division-problems.md)。
