---
title: CA2002:不要锁定具有弱标识的对象 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 631979309d9ad42a25b244e8806e5a6849f8b81d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081451"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002:不要锁定具有弱标识的对象
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|类别|Microsoft.Reliability|
|是否重大更改|非换行|

## <a name="cause"></a>原因
 一个线程尝试获取具有弱标识的对象上的锁。

## <a name="rule-description"></a>规则说明
 当可以跨应用程序域边界直接进行访问对象时，则认为该对象具有弱标识。 对于尝试获取对具有弱标识的对象的锁的线程，该线程可能会被其他应用程序域中持有对同一对象的锁的另一线程所阻止。 下面的类型具有弱标识，该规则标记：

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.String>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复此规则的冲突，请使用来自不在列表中的说明部分中的类型的对象。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。

## <a name="related-rules"></a>相关的规则
 [CA2213：应释放可释放的字段](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>示例
 下面的示例演示一些违反规则的对象锁。

 [!code-csharp[FxCop.Reliability.LockWeakObjects#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/cs/FxCop.Reliability.LockWeakObjects.cs#1)]
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/vb/FxCop.Reliability.LockWeakObjects.vb#1)]

## <a name="see-also"></a>请参阅
 <xref:System.Threading.Monitor> <xref:System.AppDomain>
 [lock 语句](http://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) [SyncLock 语句](http://msdn.microsoft.com/library/14501703-298f-4d43-b139-c4b6366af176)
