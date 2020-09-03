---
title: 在文本模板中使用转义序列 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a45aa36ddce57141a7e1e851f7f0766b77015ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659418"
---
# <a name="using-escape-sequences-in-text-templates"></a>在文本模板中使用转义序列
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在文本模板中使用转义序列来生成文本模板标记，并在 c # 代码中 (仅) 来转义控制字符和引号。

 若要将标准代码块的打开和关闭标记打印到输出文件，请按如下所示对标记进行转义：

```
\<# ... \#>
```

 您可以对其他文本模板指令和代码块标记执行相同的操作。

 如果文本块包含用于转义文本模板标记的字符串，则可以使用以下转义序列：

- 如果文本模板标记前面有偶数个转义 (\\) 字符，则模板分析器将包含一半转义符，并将序列作为文本模板标记包含在内。 例如，如果文本模板中有四个转义符，则生成的文件中将有两个 " \\ " 字符。

- 如果文本模板标记前面有奇数个转义 (\\) 字符，则模板分析器将包括部分 " \\ " 字符以及标记本身， (\<# or #>) 。 标记不被视为文本模板标记。

- 如果转义 (\\) 字符出现在除在 c) # 中转义控制字符或引用 (引号以外的任何其他序列中的其他任何位置，则将直接输出该字符。

## <a name="see-also"></a>另请参阅
 [如何：使用转义序列基于模板生成模板](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
