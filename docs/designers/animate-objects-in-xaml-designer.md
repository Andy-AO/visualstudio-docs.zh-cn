---
title: 在 XAML 设计器中动态显示对象
ms.date: 04/11/2018
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: a5bd9c24351201d066f9055554468939df02b33e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927020"
---
# <a name="animate-objects-in-xaml-designer"></a>在 XAML 设计器中动态显示对象

可以创建移动对象或使它们淡入和淡出的简短动画。

若要开始，请创建 *情节提要*。 情节提要包含一个或多个 *时间线*。 在时间线上设置 *关键帧* 以标记属性更改。 随后在运行动画时，Blend 将在指定时间段内插入属性更改。 这样便可实现平滑过渡。 可以对属于对象的任何属性（甚至非可视属性）进行动画处理。

下图显示了一个名为“MoveUp” 的情节提要。 时间线包含标记矩形的 X 和 Y 位置的关键帧。 当此动画运行时，矩形平滑地从一个位置移动到另一个位置。

![XAML 设计器中的 MoveUp 情节提要](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png)

## <a name="see-also"></a>请参阅

- [使用 Blend for Visual Studio 创建 UI](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)