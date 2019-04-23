---
title: CA2243:应正确分析特性字符串文本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f23db8a9674de621090be70067a555ef4fca2b99
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061412"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243:特性字符串文本应正确分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|类别|Microsoft.Usage|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因
 为 URL、 GUID 或版本不正确分析特性字符串文本参数。

## <a name="rule-description"></a>规则说明
 由于属性派生自<xref:System.Attribute?displayProperty=fullName>，并在编译时使用属性，只有常量值可以传递给其构造函数。 特性参数必须表示 Url、 Guid 和版本不能类型化为<xref:System.Uri?displayProperty=fullName>， <xref:System.Guid?displayProperty=fullName>，和<xref:System.Version?displayProperty=fullName>，因为这些类型不能表示为常量。 相反，它们必须由字符串表示。

 由于该参数被类型化为一个字符串，所以有可能，无法在编译时传递一个格式不正确的参数。

 此规则使用命名的启发式方法来查找参数，用于表示统一资源标识符 (URI)，全局唯一标识符 (GUID) 或版本，并验证传递的值正确。

## <a name="how-to-fix-violations"></a>如何解决冲突
 将参数字符串更改为格式正确的 URL、 GUID 或版本。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 它可以安全地禁止显示此规则的警告，如果该参数不表示 URL、 GUID 或版本。

## <a name="example"></a>示例
 下面的示例显示 AssemblyFileVersionAttribute 违反此规则的代码。

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 通过以下方法触发此规则：

- 包含版本，并且不能解析为 System.Version 的参数。

- 包含 guid 并且不能解析为 System.Guid 的参数。

- 参数包含 uri、 urn 或 url 并不能解析为 System.Uri。

## <a name="see-also"></a>请参阅
 [CA1054:URI 参数不应为字符串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
