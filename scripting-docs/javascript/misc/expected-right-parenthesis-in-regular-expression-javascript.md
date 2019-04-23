---
title: 预期) 中的正则表达式 (JavaScript) |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5de54ac2a698cd2536dadbf042554cf70502d92b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076677"
---
# <a name="expected--in-regular-expression-javascript"></a>正则表达式中应有“)”(JavaScript)
试图创建正则表达式捕获、 断言或组，但不是包括右括号。 括号的正则表达式中具有多个用途。 首先，它们用来捕获子表达式，若要指定断言，或将模式组合在一起，以便可以将项视为单个单元通过 *，+、？、，等等。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
- 添加最右侧的右括号。  
  
    > [!NOTE]
    >  如果您希望匹配单个括号，对其进行转义反斜杠- \\(-，以便它不被视为特殊字符的[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。  
  
## <a name="see-also"></a>请参阅  
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [正则表达式语法 (JavaScript)](https://msdn.microsoft.com/library/1400241x)