---
title: CA1023：索引器不应为多维索引 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30eee67d54e4fc3c73b265240fff82b0729e1cfc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546638"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023:索引器不应是多维的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|项|值|
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|类别|Microsoft. Design|
|是否重大更改|重大|

## <a name="cause"></a>原因
 公共或受保护类型包含一个使用多个索引的公共或受保护索引器。

## <a name="rule-description"></a>规则描述
 索引器（即索引属性）应使用单个索引。 多维索引器可能会显著降低库的可用性。 如果设计需要多个索引，请重新考虑该类型是否表示逻辑数据存储区。 否则，请使用方法。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复与此规则的冲突，请将设计更改为使用单独的整数或字符串索引，或使用方法而不是索引器。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 仅在仔细考虑非标准索引器的需求之后，禁止显示此规则发出的警告。

## <a name="example"></a>示例
 下面的示例演示一个类型， `DayOfWeek03` 该类型具有与规则冲突的多维索引器。 索引器可被视为一种类型的转换，因此更适合作为方法公开。 此类型在中进行了重新设计 `RedesignedDayOfWeek03` ，以满足规则。

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>相关规则
 [CA1043:将整型或字符串参数用于索引器](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024:在适用处使用属性](../code-quality/ca1024-use-properties-where-appropriate.md)
