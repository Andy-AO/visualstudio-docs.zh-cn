---
title: CA1804：删除未使用的局部变量 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4bd57d76acd0c46e39bb2c01449146715abc0666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543879"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804:移除未使用的局部变量
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|项|值|
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|类别|Microsoft. 性能|
|是否重大更改|不间断|

## <a name="cause"></a>原因
 一个方法声明一个局部变量，但不使用除这种变量之外的变量，因为它可能作为赋值语句的接收方。 对于此规则进行的分析，必须使用调试信息生成经过测试的程序集，并且 ( 的关联程序数据库必须可用) 文件。

## <a name="rule-description"></a>规则描述
 未使用的局部变量和不必要的赋值会增加程序集的大小并降低性能。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复与此规则的冲突，请删除或使用局部变量。 请注意，在启用选项后，附带的 c # 编译器会 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 删除未使用的局部变量 `optimize` 。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 如果编译器发出了编译器，则禁止显示此规则发出的警告。 如果性能和代码维护不是主要考虑因素，则可以安全地禁止显示此规则发出的警告或禁用规则。

## <a name="example"></a>示例
 下面的示例显示了几个未使用的局部变量。

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>相关规则
 [CA1809:避免过多的局部变量](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811:避免使用未调用的私有代码](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812:避免未实例化的内部类](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801:检查未使用的参数](../code-quality/ca1801-review-unused-parameters.md)
