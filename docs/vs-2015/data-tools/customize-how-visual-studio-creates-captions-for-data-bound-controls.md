---
title: 自定义 Visual Studio 2015 为数据绑定控件创建标题的方式 |Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c0e54f68ab7e34f1cfb6abb228f552cc3792a8b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476921"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>自定义 Visual Studio 创建数据绑定控件的标题的方式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

将项从 " [数据源" 窗口](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) 拖动到 Windows 窗体设计器时，需要特别注意：在发现两个或多个单词一起连接时，标题标签中的列名将重新格式化为可读性更强的字符串。 可以通过在**HKEY_CURRENT_USER \Software\microsoft\visualstudio\10.0\data 设计器**注册表项中设置**SmartCaptionExpression**、 **SmartCaptionReplacement**和**SmartCaptionSuffix**值来自定义创建这些标签的方式。

> [!NOTE]
> 在你创建此注册表项之前，此注册表项不存在。

 智能字幕由输入到 **SmartCaptionExpression** 值值的正则表达式控制。 添加 **数据设计器** 注册表项会重写控件标题标签的默认正则表达式。 有关正则表达式的详细信息，请参阅 [在 Visual Studio 中使用正则表达式](../ide/using-regular-expressions-in-visual-studio.md)。

 下表介绍了控制标题标签的注册表值。

|注册表项|说明|
|-------------------|-----------------|
|**SmartCaptionExpression**|用于匹配模式的正则表达式。|
|**SmartCaptionReplacement**|用于显示在 **SmartCaptionExpression**中匹配的所有组的格式。|
|**SmartCaptionSuffix**|要追加到标题末尾的可选字符串。|

 下表列出了这些注册表值的内部默认设置。

|注册表项|默认值|说明|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**| (\\ \p{Ll} ) # B2 \\ \p{Lu} ) # A0_ +|匹配后跟一个大写字符或下划线的小写字符。|
|**SmartCaptionReplacement**|$1 $2|$1 表示表达式的第一个括号中匹配的任何字符，$2 表示在第二个括号中匹配的任何字符。 替换为第一个匹配项、一个空格，然后第二个匹配项。|
|**SmartCaptionSuffix**|:|表示追加到返回的字符串的字符。 例如，如果标题为 `Company Name` ，则后缀使其 `Company Name:`|

> [!CAUTION]
> 在注册表编辑器中执行任何操作时，应非常小心。 在编辑注册表之前对其进行备份。 如果不正确地使用注册表编辑器，可能会导致严重问题，可能需要重新安装操作系统。 Microsoft 不保证使用注册表编辑器导致的问题可以得到解决。 你自行承担使用注册表编辑器的风险。

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>修改 "数据源" 窗口的智能标题行为

1. 通过单击 " **开始** "，然后单击 " **运行**" 打开命令窗口。

2. `regedit`在 "**运行**" 对话框中键入，然后单击 **"确定"**。

3. 展开 " **HKEY_CURRENT_USER** " 节点。

4. 展开 " **软件** " 节点。

5. 展开 " **Microsoft** " 节点。

6. 展开 " **VisualStudio** " 节点。

7. 右键单击**10.0**节点，并创建一个名为的**Key**新密钥 `Data Designers` 。

8. 右键单击 " **数据设计器** " 节点，并创建一个名为的新 **字符串值** `SmartCaptionExpression` 。

9. 右键单击 " **数据设计器** " 节点，并创建一个名为的新 **字符串值** `SmartCaptionReplacement` 。

10. 右键单击 " **数据设计器** " 节点，并创建一个名为的新 **字符串值** `SmartCaptionSuffix` 。

11. 右键单击 " **SmartCaptionExpression** " 项，然后选择 " **修改**"。

12. 输入希望 " **数据源** " 窗口使用的正则表达式。

13. 右键单击 " **SmartCaptionReplacement** " 项，然后选择 " **修改**"。

14. 输入用来显示正则表达式中匹配模式的格式的替换字符串。

15. 右键单击 " **SmartCaptionSuffix** " 项，然后选择 " **修改**"。

16. 输入要在标题末尾显示的任何字符。

     下一次从 " **数据源** " 窗口拖动项时，将使用提供的新注册表值创建标题标签。

### <a name="to-turn-off-the-smart-captioning-feature"></a>关闭智能字幕功能

1. 通过单击 " **开始** "，然后单击 " **运行**" 打开命令窗口。

2. `regedit`在 "**运行**" 对话框中键入，然后单击 **"确定"**。

3. 展开 " **HKEY_CURRENT_USER** " 节点。

4. 展开 " **软件** " 节点。

5. 展开 " **Microsoft** " 节点。

6. 展开 " **VisualStudio** " 节点。

7. 右键单击**10.0**节点，并创建一个名为的**Key**新密钥 `Data Designers` 。

8. 右键单击 " **数据设计器** " 节点，并创建一个名为的新 **字符串值** `SmartCaptionExpression` 。

9. 右键单击 " **数据设计器** " 节点，并创建一个名为的新 **字符串值** `SmartCaptionReplacement` 。

10. 右键单击 " **数据设计器** " 节点，并创建一个名为的新 **字符串值** `SmartCaptionSuffix` 。

11. 右键单击 " **SmartCaptionExpression** " 项，然后选择 " **修改**"。

12. 输入 `(.*)` 作为值。 这将匹配整个字符串。

13. 右键单击 " **SmartCaptionReplacement** " 项，然后选择 " **修改**"。

14. 输入 `$1` 作为值。 这会将字符串替换为匹配的值，这是整个字符串，因此它将保持不变。

     下一次从 " **数据源** " 窗口拖动项时，将创建带有未修改标题的标题标签。

## <a name="see-also"></a>另请参阅
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)
