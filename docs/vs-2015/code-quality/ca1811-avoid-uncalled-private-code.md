---
title: CA1811：避免使用未调用专用代码 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 223b2ff9aa25ddd94a3c62eb9e641127a1cace4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543814"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811:避免使用未调用的私有代码
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|项|值|
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|类别|Microsoft. 性能|
|是否重大更改|不间断|

## <a name="cause"></a>原因
 私有或内部 (程序集级别) 成员在程序集中没有调用方，公共语言运行时不会调用该程序集，也不会由委托调用。 此规则不检查以下成员：

- 显式接口成员。

- 静态构造函数。

- 序列化构造函数。

- 用或标记的方法 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 。

- 要重写的成员。

## <a name="rule-description"></a>规则描述
 如果出现不是由规则逻辑标识的入口点，则此规则可报告误报。 此外，编译器可能会将 noncallable 代码发送到程序集。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复与此规则的冲突，请删除 noncallable 代码或添加调用它的代码。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 可以安全地禁止显示此规则发出的警告。

## <a name="related-rules"></a>相关规则
 [CA1812:避免未实例化的内部类](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801:检查未使用的参数](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804:移除未使用的局部变量](../code-quality/ca1804-remove-unused-locals.md)
