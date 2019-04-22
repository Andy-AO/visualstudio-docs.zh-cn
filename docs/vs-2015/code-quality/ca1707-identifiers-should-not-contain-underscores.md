---
title: CA1707:标识符不应包含下划线 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7973646aab545484287f5628eb0fa3cf3629db84
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59651940"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707:标识符不应包含下划线
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 的最新文档，请参阅[CA1707:标识符不应包含下划线](https://docs.microsoft.com/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores)。  
  
|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|类别|Microsoft.Naming|  
|是否重大更改|-对程序集引发时中断<br /><br /> 无间断-类型参数上发生|  
  
## <a name="cause"></a>原因  
 标识符名称包含下划线 (_) 字符。  
  
## <a name="rule-description"></a>规则说明  
 按照约定，标识符名称不包含下划线 (_) 字符。 此规则检查命名空间、 类型、 成员和参数。  
  
 命名约定提供了通用的外观对于库面向公共语言运行时。 这会减少所需的新软件库，并会增加客户信心库由必须在托管代码中开发的专业知识的人学习曲线。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 从名称中删除所有下划线字符。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1709:标识符应采用正确的大小写](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708:标识符不应不同于用例的详细信息](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
