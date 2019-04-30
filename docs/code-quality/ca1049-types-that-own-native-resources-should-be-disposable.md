---
title: CA1049:拥有本机资源的类型应是可释放的
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- cplusplus
ms.openlocfilehash: 41ab039d33155769eac13469a65f2a35c8ed7324
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778601"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049:拥有本机资源的类型应是可释放的

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|类别|Microsoft.Design|
|是否重大更改|非换行|

## <a name="cause"></a>原因

一种类型引用<xref:System.IntPtr?displayProperty=fullName>字段中，<xref:System.UIntPtr?displayProperty=fullName>字段中，或<xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>字段中，但不实现<xref:System.IDisposable?displayProperty=fullName>。

## <a name="rule-description"></a>规则说明

此规则假定<xref:System.IntPtr>， <xref:System.UIntPtr>，和<xref:System.Runtime.InteropServices.HandleRef>字段存储指向非托管资源。 分配非托管的资源的类型应实现<xref:System.IDisposable>让调用方释放这些资源按需和缩短持有这些资源的对象的生存期。

要清理非托管资源的建议的设计模式是提供一种隐式和显式方式释放这些资源通过<xref:System.Object.Finalize%2A?displayProperty=fullName>方法和<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法，分别。 垃圾回收器调用<xref:System.Object.Finalize%2A>在不确定的时间段后该对象被确定为不再可访问一个对象的方法。 之后<xref:System.Object.Finalize%2A>调用时，其他释放该对象所需的垃圾回收。 <xref:System.IDisposable.Dispose%2A>方法允许调用方来显式释放资源按需、 早于将释放的资源，如果从左到垃圾回收器。 清理非托管资源之后,<xref:System.IDisposable.Dispose%2A>应调用<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>方法，用于通知垃圾回收器知道<xref:System.Object.Finalize%2A>不再具有要调用; 这就不必进行其他垃圾回收并缩短了对象的生存期。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复此规则的冲突，请实现<xref:System.IDisposable>。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 它可以安全地禁止显示此规则的警告，如果类型不引用非托管的资源。 否则，不要禁止显示此规则的警告因为未能实现<xref:System.IDisposable>可能会导致非托管的资源变得不可用或未充分利用。

## <a name="example"></a>示例
 下面的示例演示实现的类型<xref:System.IDisposable>以清理非托管资源。

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>相关的规则
 [CA2115:调用 GC。使用本机资源时保持连接](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816:调用 GC。SuppressFinalize 正确](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216:可释放类型应声明终结器](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001：具有可释放字段的类型应该是可释放的](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>请参阅

- [清理未托管资源](/dotnet/standard/garbage-collection/unmanaged)（清理未托管资源）
- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)