---
title: CA1900：值类型字段应为可移植 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ece4788a277bfc4d16568d4014f9eae2ed4de33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545270"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900:值类型字段应为可移植字段
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

有关 Visual Studio 的最新文档，请参阅 [CA1900：值类型字段应为可移植字段](/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable)。

|项|值|
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|类别|Microsoft 可移植性|
|是否重大更改|如果该字段可以在程序集外查看，则为。<br /><br /> 无间断-如果该字段在程序集外部不可见，则为。|

## <a name="cause"></a>原因
 此规则检查在被封送到64位操作系统上的非托管代码时，通过显式布局声明的结构是否会正确对齐。 IA-64 不允许未对齐的内存访问，如果不解决此冲突，进程将崩溃。

## <a name="rule-description"></a>规则描述
 具有包含未对齐字段的显式布局的结构会导致在64位操作系统上发生崩溃。

## <a name="how-to-fix-violations"></a>如何解决冲突
 小于8个字节的所有字段的偏移量必须是其大小的倍数，而大于8个字节或更大的字段的偏移量必须是8的倍数。 另一种解决方案是使用 `LayoutKind.Sequential` 而不是 `LayoutKind.Explicit` ，前提是合理。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 只有出现错误时才应禁止显示此警告。
