---
title: CA1003：使用泛型事件处理程序实例 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ee0571e85a1d4ec9960e0235814fcb9d7adbd483
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539901"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003:使用泛型事件处理程序实例
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|项|值|
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|类别|Microsoft. Design|
|是否重大更改|重大|

## <a name="cause"></a>原因
 类型包含一个返回 void 的委托，该委托的签名包含 (第一个对象的两个参数，第二个参数包含可分配给 EventArgs) 的类型和包含程序集目标 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 。

## <a name="rule-description"></a>规则描述
 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]在之前，若要将自定义信息传递到事件处理程序，必须将新委托声明为指定派生自类的类 <xref:System.EventArgs?displayProperty=fullName> 。 这在引入委托的中不再是如此 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] <xref:System.EventHandler%601?displayProperty=fullName> 。 此泛型委托允许将派生自的任何类 <xref:System.EventArgs> 与事件处理程序一起使用。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复与此规则的冲突，请删除委托，并使用委托替换其使用 <xref:System.EventHandler%601?displayProperty=fullName> 。 如果委托由编译器自动生成 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ，请更改事件声明的语法以使用 <xref:System.EventHandler%601?displayProperty=fullName> 委托。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。

## <a name="example"></a>示例
 下面的示例演示了违反规则的委托。 在此 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 示例中，注释说明了如何修改示例以满足规则。 对于 c # 示例，下面的示例演示了修改后的代码。

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>示例
 下面的示例从上一个示例中删除委托声明，该声明满足规则，并 `ClassThatRaisesEvent` 使用委托替换和方法中的使用 `ClassThatHandlesEvent` <xref:System.EventHandler%601?displayProperty=fullName> 。

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>相关规则
 [CA1005:避免泛型类型的参数过多](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010:集合应实现泛型接口](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000:不要在泛型类型中声明静态成员](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002:不要公开泛型列表](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006:不要将泛型类型嵌套在成员签名中](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004:泛型方法应提供类型参数](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007:在适用处使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另请参阅
 [泛型](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
