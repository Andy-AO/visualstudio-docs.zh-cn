---
title: CA2220：终结器应调用基类的终结器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5d9139314d52c4c50de84a45f227e6df5715bf02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540655"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220:终结器应调用基类的终结器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|项|值|
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|类别|Microsoft. 使用情况|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因
 重写的类型 <xref:System.Object.Finalize%2A?displayProperty=fullName> 不会 <xref:System.Object.Finalize%2A> 在其基类中调用方法。

## <a name="rule-description"></a>规则描述
 终止必须通过继承层次结构传播。 若要确保这一点，类型必须 <xref:System.Object.Finalize%2A> 从其自身的方法中调用其基类方法 <xref:System.Object.Finalize%2A> 。 C # 编译器自动添加对基类终结器的调用。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复与此规则的冲突，请从方法中调用基类型的 <xref:System.Object.Finalize%2A> 方法 <xref:System.Object.Finalize%2A> 。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。 针对公共语言运行时的某些编译器会将对基类型的终结器的调用插入到 Microsoft 中间语言 (MSIL) 。 如果报告了此规则发出的警告，则编译器不会插入调用，你必须将其添加到你的代码中。

## <a name="example"></a>示例
 下面的 Visual Basic 示例显示了一个 `TypeB` 正确调用 <xref:System.Object.Finalize%2A> 其基类中的方法的类型。

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>另请参阅
 [释放模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
