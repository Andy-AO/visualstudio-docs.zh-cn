---
title: CA2230：对变量参数使用参数 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ce66e04272618b9df2ab1957af305bb9bf40ee9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540356"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230:对可变数量的参数使用 params
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|项|值|
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|类别|Microsoft. 使用情况|
|是否重大更改|重大|

## <a name="cause"></a>原因
 公共或受保护类型包含使用调用约定的公共或受保护方法 `VarArgs` 。

## <a name="rule-description"></a>规则描述
 `VarArgs`调用约定用于采用可变数量的参数的某些方法定义。 使用 `VarArgs` 调用约定的方法不是公共语言规范 (符合 CLS) 并且可能无法跨编程语言访问。

 在 c # 中，在 `VarArgs` 方法的参数列表以关键字结尾时使用调用约定 `__arglist` 。 Visual Basic 不支持 `VarArgs` 调用约定，并且 Visual C++ 只允许在使用椭圆表示法的非托管代码中使用 `...` 。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复 c # 中与此规则的冲突，请使用 [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) 关键字而不是 `__arglist` 。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。

## <a name="example"></a>示例
 下面的示例演示了两种方法，一个是违反规则的方法，另一个是满足规则的方法。

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>另请参阅
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [语言独立性和与语言无关的组件](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
