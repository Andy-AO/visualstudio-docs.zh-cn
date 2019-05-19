---
title: CA1815:重写值类型上的 Equals 和相等运算符
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58d746b022d5cc3f67b53e1dc845d81bf8409ec6
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841483"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815:重写值类型上的 Equals 和相等运算符

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|类别|Microsoft.Performance|
|是否重大更改|非换行|

## <a name="cause"></a>原因

值类型不重写<xref:System.Object.Equals%2A?displayProperty=fullName>或未实现相等运算符 （= =）。 此规则不会检查枚举。

默认情况下，此规则只看起来在外部可见的类型，但这是[可配置](#configurability)。

## <a name="rule-description"></a>规则说明

对于值类型，继承的实现<xref:System.Object.Equals%2A>使用反射库，并将所有字段的内容进行比较。 反射需要消耗大量计算资源，可能没有必要比较每一个字段是否相等。 如果期望用户比较或排序的实例，或将它们用作哈希表键，则值类型应实现<xref:System.Object.Equals%2A>。 如果编程语言支持运算符重载，则还应提供相等和不等运算符的实现。

## <a name="how-to-fix-violations"></a>如何解决冲突

若要修复此规则的冲突，请提供的实现<xref:System.Object.Equals%2A>。 如果可以实现相等运算符。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

它可以安全地禁止显示此规则的警告，如果不相互进行比较的值类型的实例。

## <a name="configurability"></a>可配置性

如果您运行此规则与[FxCop 分析器](install-fxcop-analyzers.md)（而不是通过静态代码分析），你可以配置的哪些部分在基本代码，以运行此规则，基于其可访问性。 例如，若要指定该规则应运行仅对非公共 API 外围应用，请到您的项目中的.editorconfig 文件添加以下键-值对：

```ini
dotnet_code_quality.ca1815.api_surface = private, internal
```

此类别 （性能） 中，可以配置此选项只是此规则，所有规则，或所有规则。 有关详细信息，请参阅[配置 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>示例

下面的代码显示了与此规则冲突的结构 （值类型）：

[!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]

下面的代码修复通过重写前面的冲突<xref:System.ValueType.Equals%2A?displayProperty=fullName>和实现相等运算符 (= =、 ！ =):

[!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]

## <a name="related-rules"></a>相关的规则

- [CA2224:重写 equals 方法重载相等运算符](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2231：重写 ValueType.Equals 时应重载相等运算符](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
- [CA2226:运算符应有对称重载](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>请参阅

- <xref:System.Object.Equals%2A?displayProperty=fullName>