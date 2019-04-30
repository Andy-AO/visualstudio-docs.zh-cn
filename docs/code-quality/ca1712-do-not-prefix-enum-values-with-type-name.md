---
title: CA1712:不要将类型名用作枚举值的前缀
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dd15e582f7654f82e343a0175ccf9ed18254d904
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545865"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712:不要将类型名用作枚举值的前缀

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|类别|Microsoft.Naming|
|是否重大更改|重大|

## <a name="cause"></a>原因
 一个枚举，包含作为名称开头的枚举类型名称的成员。

## <a name="rule-description"></a>规则说明
 由于类型信息需要由开发工具提供的枚举成员的名称将不使用前缀的类型名称。

 命名约定提供了通用的外观对于库面向公共语言运行时。 这将减少需要，若要了解新的软件库，并且会增加客户信心库由在托管代码开发具有专业知识的人员的时间。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要解决此规则的冲突，请从该枚举成员中删除类型名称前缀。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。

## <a name="example"></a>示例
 下面的示例演示的修正版本后跟一个未正确命名的枚举。

 [!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
 [!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
 [!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>相关的规则
 [CA1711:标识符应采用正确的后缀](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027:用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217:不使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>请参阅

- <xref:System.Enum?displayProperty=fullName>