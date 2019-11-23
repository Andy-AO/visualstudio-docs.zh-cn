---
title: 应输入日期对象 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10af48c4804df3b5513df71578b948abe73ff8c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572897"
---
# <a name="date-object-expected"></a>缺少日期对象
您尝试对 `Date`以外的类型的对象调用**valueOf** **方法，而不是调用**。 此类调用的对象必须是 `Date`类型。 例如：  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
- 仅在 `Date`**类型的对象**上调用 valueOf 方法或方法。  
  
## <a name="see-also"></a>另请参阅  
 [Date 对象](../../javascript/reference/date-object-javascript.md)   
 [GetDate 方法（Date）](../../javascript/reference/getdate-method-date-javascript.md)   
 [内部对象](../../javascript/intrinsic-objects-javascript.md)