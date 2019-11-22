---
title: 'CA1065: Do not raise exceptions in unexpected locations | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 439c6b5fc30be2e76eb6c0b6a44b1ec5226633b1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295942"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065：不要在意外的位置引发异常
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|类别|Microsoft.Design|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因
 不应引发异常的方法引发了异常。

## <a name="rule-description"></a>规则说明
 Methods that are not expected to throw exceptions can be categorized as follows:

- Property Get Methods

- 事件访问器方法

- Equals Methods

- GetHashCode Methods

- ToString Methods

- 静态构造函数

- 终结器

- Dispose Methods

- 相等运算符

- Implicit Cast Operators

  The following sections discuss these method types.

### <a name="property-get-methods"></a>Property Get Methods
 Properties are basically smart fields. Therefore, they should behave like a field as much as possible. Fields do not throw exceptions and neither should properties. If you have a property that throws an exception, consider making it a method.

 The following exceptions are allowed to be thrown from a property get method:

- <xref:System.InvalidOperationException?displayProperty=fullName> and all derivatives (including <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> and all derivatives

- <xref:System.ArgumentException?displayProperty=fullName> (only from indexed get)

- <xref:System.Collections.Generic.KeyNotFoundException> (only from indexed get)

### <a name="event-accessor-methods"></a>事件访问器方法
 Event accessors should be simple operations that do not throw exceptions. An event should not throw an exception when you try to add or remove an event handler.

 The following exceptions are allowed to be thrown from an event accesor:

- <xref:System.InvalidOperationException?displayProperty=fullName> and all derivatives (including <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> and all derivatives

- <xref:System.ArgumentException> and derivatives

### <a name="equals-methods"></a>Equals Methods
 The following **Equals** methods should not throw exceptions:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- [M:IEquatable.Equals](https://go.microsoft.com/fwlink/?LinkId=113472)

  An **Equals** method should return `true` or `false` instead of throwing an exception. For example, if Equals is passed two mismatched types it should just return `false` instead of throwing an <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>GetHashCode Methods
 The following **GetHashCode** methods should usually not throw exceptions:

- <xref:System.Object.GetHashCode%2A>

- [M:IEqualityComparer.GetHashCode(T)](https://go.microsoft.com/fwlink/?LinkId=113477)

  **GetHashCode** should always return a value. Otherwise, you can lose items in the hash table.

  The versions of **GetHashCode** that take an argument can throw an <xref:System.ArgumentException>. However, **Object.GetHashCode** should never throw an exception.

### <a name="tostring-methods"></a>ToString Methods
 The debugger uses <xref:System.Object.ToString%2A?displayProperty=fullName> to help display information about objects in string format. Therefore, **ToString** should not change the state of an object and it should not throw exceptions.

### <a name="static-constructors"></a>静态构造函数
 Throwing exceptions from a static constructor causes the type to be unusable in the current application domain. You should have a very good reason (such as a security issue) for throwing an exception from a static constructor.

### <a name="finalizers"></a>终结器
 Throwing an exception from a finalizer causes the CLR to fail fast, which tears down the process. Therefore, throwing exceptions in a finalizer should always be avoided.

### <a name="dispose-methods"></a>Dispose Methods
 A <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> method should not throw an exception. Dispose is often called as part of the clean up logic in a `finally` clause. Therefore, explicitly throwing an exception from Dispose forces the user to add exception handling inside the `finally` clause.

 The **Dispose(false)** code path should never throw exceptions, because this is almost always called from a finalizer.

### <a name="equality-operators--"></a>Equality Operators (==, !=)
 Like Equals methods, equality operators should return either `true` or `false` and should not throw exceptions.

### <a name="implicit-cast-operators"></a>Implicit Cast Operators
 Because the user is often unaware that an implicit cast operator has been called, an exception thrown by the implicit cast operator is completely unexpected. Therefore, no exceptions should be thrown from implicit cast operators.

## <a name="how-to-fix-violations"></a>如何解决冲突
 For property getters, either change the logic so that it no longer has to throw an exception, or change the property into a method.

 For all other method types listed previously, change the logic so that it no longer must throw an exception.

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 It is safe to suppress a warning from this rule if the violation was caused by an exception declaration instead of a thrown exception.

## <a name="related-rules"></a>Related Rules
 [CA2219：在异常子句中不引发异常](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>请参阅
 [设计警告](../code-quality/design-warnings.md)
