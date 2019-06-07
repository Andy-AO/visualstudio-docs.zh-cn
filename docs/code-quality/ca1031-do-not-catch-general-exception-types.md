---
title: CA1031:不要捕捉一般异常类型
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e9746119c746679817076c86e3d5a9080cec30d9
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744686"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031:不要捕捉一般异常类型

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|类别|Microsoft.Design|
|是否重大更改|非换行|

## <a name="cause"></a>原因
 如一般异常<xref:System.Exception?displayProperty=fullName>或<xref:System.SystemException?displayProperty=fullName>陷入`catch`语句或常规 catch 子句，如`catch()`使用。

## <a name="rule-description"></a>规则说明
 不应捕捉一般异常。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要解决此规则的冲突，捕获更具体的异常，或重新引发一般异常中的最后一个语句`catch`块。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。 捕捉一般异常类型可以隐藏运行时库用户问题，并且可能使调试更加困难。

> [!NOTE]
> 从.NET Framework 4 开始，公共语言运行时 (CLR) 不再提供操作系统和托管的代码中，例如，在访问冲突中发生的损坏的状态异常[!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]、 要由托管代码。 如果您想进行编译的应用程序中的.NET Framework 4 或更高版本和维护的损坏的状态异常的处理，则可以应用<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>属性为负责处理损坏的状态异常的方法。

## <a name="example"></a>示例
 下面的示例显示了违反此规则的类型，并正确实现的类型`catch`块。

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>相关的规则
 [CA2200:再次引发以保留堆栈详细信息](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)