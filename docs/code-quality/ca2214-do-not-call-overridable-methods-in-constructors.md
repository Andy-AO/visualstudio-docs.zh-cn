---
title: CA2214:不要在构造函数中调用可重写的方法
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ef2a5631247f882a70ae94877da02f576ff04a5d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796700"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214:不要在构造函数中调用可重写的方法

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|类别|Microsoft.Usage|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因

未密封的类型的构造函数调用在其类中定义的虚方法。

## <a name="rule-description"></a>规则说明

当调用虚方法时，直到运行时未选择执行该方法的实际类型。 当构造函数调用虚方法时，就可以调用该方法的实例的构造函数不执行。

## <a name="how-to-fix-violations"></a>如何解决冲突

若要解决此规则的冲突，请勿调用类型的从该类型的构造函数内的虚拟方法。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

不禁止显示此规则发出的警告。 构造函数应重新设计，以消除对虚拟方法的调用。

## <a name="example"></a>示例

下面的示例演示了违反此规则的效果。 测试应用程序创建的实例`DerivedType`，这将导致其基类 (`BadlyConstructedType`) 构造函数来执行。 `BadlyConstructedType`构造函数不正确调用虚拟方法`DoSomething`。 如输出所示，`DerivedType.DoSomething()`执行，并且因此之前是`DerivedType`的构造函数执行。

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

该示例产生下面的输出：

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```