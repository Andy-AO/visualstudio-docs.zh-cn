---
title: CA2201：不要引发保留的异常类型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9533a597a33deaed17ff2a73d56ef306ea7b5613
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546336"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201:不要引发保留的异常类型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|项|值|
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|类别|Microsoft. 使用情况|
|是否重大更改|重大|

## <a name="cause"></a>原因
 方法引发的异常类型太笼统或由运行时保留。

## <a name="rule-description"></a>规则描述
 以下异常类型太一般，无法为用户提供足够的信息：

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

  以下异常类型已保留，只应由公共语言运行时引发：

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

  **不引发一般异常**

  如果在库或框架中引发一般异常类型（如 <xref:System.Exception> 或） <xref:System.SystemException> ，则它会强制使用者捕获所有异常，包括不知道如何处理的未知异常。

  相反，引发框架中已存在的派生程度更高的类型，或者创建您自己的派生自的类型 <xref:System.Exception> 。

  **引发特定异常**

  下表显示了参数以及在验证参数时要引发的异常，包括属性的 set 访问器中的 value 参数：

|参数说明|异常|
|---------------------------|---------------|
|`null` 对|<xref:System.ArgumentNullException?displayProperty=fullName>|
|超出允许的值范围 (例如集合或列表的索引) |<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|`enum`值无效|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|包含不满足方法参数规范的格式 (如) 的格式字符串 `ToString(String)`|<xref:System.FormatException?displayProperty=fullName>|
|否则无效|<xref:System.ArgumentException?displayProperty=fullName>|

 当操作对对象引发的当前状态无效时 <xref:System.InvalidOperationException?displayProperty=fullName>

 对已释放的引发的对象执行操作时 <xref:System.ObjectDisposedException?displayProperty=fullName>

 当不支持某个操作时 (如在重写的 **流中。写入** 打开的流以读取) 引发 <xref:System.NotSupportedException?displayProperty=fullName>

 当转换导致溢出 (如在显式转换运算符重载中) throw <xref:System.OverflowException?displayProperty=fullName>

 对于所有其他情况，可考虑创建自己的派生自的类型 <xref:System.Exception> 并引发该。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复与此规则的冲突，请将引发的异常的类型更改为非保留类型之一的特定类型。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。

## <a name="related-rules"></a>相关规则
 [CA1031:不要捕捉一般异常类型](../code-quality/ca1031-do-not-catch-general-exception-types.md)
