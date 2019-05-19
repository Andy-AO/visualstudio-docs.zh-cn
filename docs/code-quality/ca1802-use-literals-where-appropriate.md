---
title: CA1802:在合适的位置使用文本
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dfa50fc6007c2313191b430e9ed5445e7fd72a88
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841555"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802:在合适的位置使用文本

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|类别|Microsoft.Performance|
|是否重大更改|非换行|

## <a name="cause"></a>原因

字段声明`static`并`readonly`(`Shared`和`ReadOnly`在 Visual Basic 中)，并使用在编译时计算的值初始化。

默认情况下，此规则只看起来在外部可见字段，但这是[可配置](#configurability)。

## <a name="rule-description"></a>规则说明

值`static readonly`时调用的声明类型的静态构造函数，在运行时将计算字段。 如果`static readonly`字段会初始化时它声明和静态构造函数未显式声明，则编译器将发出静态构造函数来初始化该字段。

值`const`字段是在编译时计算和存储在元数据，这会增加运行时性能相比到`static readonly`字段。

因为分配给目标字段的值可在编译时，将声明更改为`const`字段，以便在编译时而不是在运行时计算的值。

## <a name="how-to-fix-violations"></a>如何解决冲突

若要解决此规则的冲突，替换`static`并`readonly`修饰符用于`const`修饰符。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

如果无需关注性能，它是安全地禁止显示此规则的警告或禁用规则。

## <a name="configurability"></a>可配置性

如果您运行此规则与[FxCop 分析器](install-fxcop-analyzers.md)（而不是通过静态代码分析），你可以配置的哪些部分在基本代码，以运行此规则，基于其可访问性。 例如，若要指定该规则应运行仅对非公共 API 外围应用，请到您的项目中的.editorconfig 文件添加以下键-值对：

```ini
dotnet_code_quality.ca1802.api_surface = private, internal
```

此类别 （性能） 中，可以配置此选项只是此规则，所有规则，或所有规则。 有关详细信息，请参阅[配置 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>示例

下面的示例演示一种类型， `UseReadOnly`，这违反了规则和一个类型， `UseConstant`，满足该规则。

[!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
[!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]