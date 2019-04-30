---
title: CA2208:正确实例化参数异常
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d82b1884336b314e8fcede3c6041030a878b999c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806759"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208:正确实例化参数异常

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|类别|Microsoft.Usage|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因

可能的原因包括以下情况：

- 调用，或其派生的异常类型的默认 （无参数） 构造函数<xref:System.ArgumentException>。

- 不正确的字符串参数传递给参数化构造函数，或其派生的异常类型的<xref:System.ArgumentException>。

## <a name="rule-description"></a>规则说明

而不是调用默认构造函数，调用允许更有意义的异常消息提供的构造函数重载之一。 异常消息应面向开发人员，并清楚地解释错误条件以及如何更正或避免异常。

一个或两个字符串的构造函数的签名<xref:System.ArgumentException>及其派生的类型而不相对于一致`message`和`paramName`参数。 请确保使用正确的字符串参数调用这些构造函数。 签名如下所示：

 <xref:System.ArgumentException>(字符串`message`)

 <xref:System.ArgumentException>(字符串`message`，字符串`paramName`)

 <xref:System.ArgumentNullException>(字符串`paramName`)

 <xref:System.ArgumentNullException>(字符串`paramName`，字符串`message`)

 <xref:System.ArgumentOutOfRangeException>(字符串`paramName`)

 <xref:System.ArgumentOutOfRangeException>(字符串`paramName`，字符串`message`)

 <xref:System.DuplicateWaitObjectException>(字符串`parameterName`)

 <xref:System.DuplicateWaitObjectException>(字符串`parameterName`，字符串`message`)

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复此规则的冲突，请调用的构造函数的一条消息、 参数名称，或两者，并确保参数是正确的类型的<xref:System.ArgumentException>被调用。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 它可以安全地禁止显示此规则的警告，如果使用正确的字符串自变量调用参数化构造函数。

## <a name="example-1"></a>示例 1
 下面的示例显示了不正确实例化 ArgumentNullException 类型的实例的构造函数。

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

## <a name="example-2"></a>示例 2
 下面的示例通过切换构造函数参数修复了上面的冲突。

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]