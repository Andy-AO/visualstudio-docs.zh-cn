---
title: CA1007:在适用处使用泛型
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ce4f72ba56b27d87d785ca561bad0de6e59dfdc2
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744769"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007:在适用处使用泛型

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|类别|Microsoft.Design|
|是否重大更改|重大|

## <a name="cause"></a>原因
 外部可见方法包含类型的引用参数<xref:System.Object?displayProperty=fullName>，和包含程序集面向.NET Framework 2.0。

## <a name="rule-description"></a>规则说明
 引用参数是一个参数，通过修改`ref`(`ByRef`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 关键字。 为引用参数提供的自变量类型必须与引用参数类型完全匹配。 若要使用派生自引用参数类型的类型，该类型必须首先进行强制转换和分配给引用参数类型的变量。 使用泛型方法，所有类型，受约束，以传递给该方法，而无需第一个强制转换为引用参数类型的类型。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要解决此规则的冲突，使该方法成为泛型函数和替换<xref:System.Object>通过使用类型参数的参数。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。

## <a name="example"></a>示例
 下面的示例演示实现为非泛型和泛型方法的常规用途的交换例程。 请注意如何有效地使用与非泛型方法的泛型方法交换字符串。

 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>相关的规则
 [CA1005:避免泛型类型参数过多](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010:集合应实现泛型接口](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000:不要在泛型类型中声明静态成员](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002:不要公开泛型列表](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006:不要将嵌套在成员签名中的泛型类型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004:泛型方法应提供类型参数](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003:使用泛型事件处理程序实例](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>请参阅
 [泛型](/dotnet/csharp/programming-guide/generics/index)