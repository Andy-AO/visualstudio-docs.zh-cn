---
title: CA2134:在重写基方法时，方法必须保持一致的透明度
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67114c20a7fcf5e8ff01773d8777b23d3caf3d91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542319"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134:在重写基方法时，方法必须保持一致的透明度

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|类别|Microsoft.Security|
|是否重大更改|重大|

## <a name="cause"></a>原因
 此规则时的方法标记为激发<xref:System.Security.SecurityCriticalAttribute>方法重写一个透明的或标有<xref:System.Security.SecuritySafeCriticalAttribute>。 是透明的或与标记的方法时，规则还会激发<xref:System.Security.SecuritySafeCriticalAttribute>重写方法将标有<xref:System.Security.SecurityCriticalAttribute>。

 该规则在重写虚方法或实现接口时应用。

## <a name="rule-description"></a>规则说明
 进行更改的方法进一步继承链安全可访问性的尝试将引发此规则。 例如，如果基类中的虚拟方法为透明或安全关键，然后派生的类必须重写它使用透明或安全关键方法。 相反，如果虚拟是安全关键的派生的类必须重写它与安全关键方法。 该规则同样适用于实现接口方法。

 执行代码，以便透明度计算不具有动态类型信息的 JIT 编译而不是在运行时，强制执行透明度规则。 因此，透明度计算结果必须能够确定仅从受 JIT 编译，而不考虑动态类型的静态类型。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要解决此规则的冲突，更改是重写虚拟方法或实现一个接口以匹配透明虚拟或接口方法的方法的透明度。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不要禁止显示此规则的警告。 违反此规则将导致运行时<xref:System.TypeLoadException>的程序集，使用 2 级透明度。

## <a name="examples"></a>示例

### <a name="code"></a>代码
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]

## <a name="see-also"></a>请参阅
 [安全透明代码，级别 2](/dotnet/framework/misc/security-transparent-code-level-2)