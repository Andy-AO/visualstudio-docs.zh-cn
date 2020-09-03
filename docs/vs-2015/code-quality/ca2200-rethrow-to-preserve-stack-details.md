---
title: CA2200：再次引发以保留堆栈详细信息 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6d63ef6ff3647742e931fd05f59c66b40059ad00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546362"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200:再次引发以保留堆栈详细信息
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|项|值|
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|类别|Microsoft. 使用情况|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因
 再次引发异常，并且在语句中显式指定了异常 `throw` 。

## <a name="rule-description"></a>规则描述
 引发异常后，它所携带的信息的一部分是堆栈跟踪。 堆栈跟踪是方法调用层次结构的一个列表，它以引发异常的方法开头，并以捕获异常的方法结束。 如果通过在语句中指定异常来重新引发异常，则将 `throw` 在当前方法处重新启动堆栈跟踪，并将丢失引发异常的原始方法和当前方法之间的方法调用的列表。 若要保留原始堆栈跟踪信息和异常，请使用 `throw` 语句而不指定异常。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复与此规则的冲突，请在不显式指定异常的情况下重新引发异常。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。

## <a name="example"></a>示例
 下面的示例演示了一个方法， `CatchAndRethrowExplicitly` 该方法违反了规则和 `CatchAndRethrowImplicitly` 满足规则的方法。

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]
