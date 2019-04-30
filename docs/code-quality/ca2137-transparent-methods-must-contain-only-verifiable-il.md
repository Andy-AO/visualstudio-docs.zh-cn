---
title: CA2137:透明方法只能包含可验证的 IL
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f74b539d9382bf8b5f5fe319ff319cdf6f372340
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806953"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137:透明方法只能包含可验证的 IL

|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|类别|Microsoft.Security|
|是否重大更改|重大|

## <a name="cause"></a>原因
 某个方法包含无法验证的代码或通过引用返回类型。

## <a name="rule-description"></a>规则说明
 在尝试通过安全透明代码执行无法验证的 MSIL（Microsoft 中间语言）时将引发此规则。 但是，此规则不包含完整的 IL 验证程序，而是使用试探法来捕捉 MSIL 验证的大部分冲突。

 若要确保你的代码包含仅可验证的 MSIL，运行[Peverify.exe （PEVerify 工具）](/dotnet/framework/tools/peverify-exe-peverify-tool)上您的程序集。 运行与 PEVerify **/ 透明**将输出限制为仅无法验证透明方法将导致错误的选项。 如果 / 不使用透明的选项，PEVerify 还会验证是否允许包含不可验证的代码的关键方法。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要解决此规则的冲突，此方法标记<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>特性，或移除不可验证的代码。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。

## <a name="example"></a>示例
 此示例中的方法使用无法验证的代码，并且应标有<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>属性。

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]