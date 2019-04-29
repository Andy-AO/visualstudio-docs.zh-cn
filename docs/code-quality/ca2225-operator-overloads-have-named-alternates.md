---
title: CA2225:运算符重载具有命名的备用项
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8a1c7015421b686d47bfea4c3341ec76748f8ad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806610"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225:运算符重载具有命名的备用项

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|类别|Microsoft.Usage|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因

检测到运算符重载，但找不到预期命名的备用方法。

默认情况下，此规则只看起来在外部可见的类型，但这是[可配置](#configurability)。

## <a name="rule-description"></a>规则说明

运算符重载允许使用的符号来表示类型的计算。 例如，添加重载加号 （+） 的类型通常具有名为 Add 的可选成员。 命名的备用成员提供对与运算符相同的功能的访问，并提供给开发人员的语言不支持重载的运算符进行编程。

此规则将检查下表中列出的运算符。

|C#|Visual Basic|C++|备用名称|
|---------|------------------|-----------|--------------------|
|+ （二进制）|+|+ （二进制）|添加|
|+=|+=|+=|添加|
|&|且|&|BitwiseAnd|
|&=|And=|&=|BitwiseAnd|
|&#124;|Or|&#124;|BitwiseOr|
|&#124;=|Or=|&#124;=|BitwiseOr|
|--|不适用|--|递减|
|/|/|/|除|
|/=|/=|/=|除|
|==|=|==|Equals|
|^|Xor|^|Xor|
|^=|Xor=|^=|Xor|
|>|>|>|比较|
|>=|>=|>=|比较|
|++|不适用|++|递增|
|<>|!=|Equals|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|比较|
|<=|<=|\<=|比较|
|&&|不适用|&&|LogicalAnd|
|&#124;&#124;|不适用|&#124;&#124;|LogicalOr|
|!|不适用|!|LogicalNot|
|%|Mod|%|Mod 或其余部分|
|%=|不适用|%=|Mod|
|* （二进制）|*|*|相乘|
|*=|不适用|*=|相乘|
|~|Not|~|OnesComplement|
|>>|>>|>>|RightShift|
=|不适用|>>=|RightShift|
|-（二进制）|-（二进制）|-（二进制）|减|
|-=|不适用|-=|减|
|true|IsTrue|不适用|IsTrue （属性）|
|-（一元）|不适用|-|求反|
|+ （一元）|不适用|+|Plus|
|False|IsFalse|False|IsTrue （属性）|

N/A = = 无法在所选语言中重载。

该规则还会检查类型中的隐式和显式强制转换运算符 (`SomeType`) 通过检查方法名为`ToSomeType`和`FromSomeType`。

在 C# 中，当重载二元运算符时，相应的赋值运算符，如果有的话，也会隐式重载。

## <a name="how-to-fix-violations"></a>如何解决冲突

若要解决此规则的冲突，实现对运算符; 的替代方法使用建议的替代名称将其命名。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

如果要实现共享的库不禁止显示此规则的警告。 应用程序可以忽略此规则的警告。

## <a name="configurability"></a>可配置性

如果您运行此规则与[FxCop 分析器](install-fxcop-analyzers.md)（而不是通过静态代码分析），你可以配置的哪些部分在基本代码，以运行此规则，基于其可访问性。 例如，若要指定该规则应运行仅对非公共 API 外围应用，请到您的项目中的.editorconfig 文件添加以下键-值对：

```
dotnet_code_quality.ca2225.api_surface = private, internal
```

此类别 （用法） 中，可以配置此选项只是此规则，所有规则，或所有规则。 有关详细信息，请参阅[配置 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>示例

下面的示例定义与此规则冲突的结构。 若要更正示例中，添加公共`Add(int x, int y)`方法的结构。

[!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>相关的规则

- [CA1046:请重载相等运算符对引用类型](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2226:运算符应有对称重载](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224:重写 equals 方法重载相等运算符](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218:重写 Equals 时重写 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231：重写 ValueType.Equals 时应重载相等运算符](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)