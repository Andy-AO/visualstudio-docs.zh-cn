---
title: CA1415:正确声明 P-Invoke
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da6448a414437a07b545a999b35031f82e9a8689
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546181"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415:正确声明 P/Invoke

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|类别|Microsoft.Interoperability|
|是否重大更改|无间断-如果 P/Invoke 声明参数不能程序集外可见。 是-如果 P/Invoke 声明该参数可以程序集外可见。|

## <a name="cause"></a>原因
 平台调用方法未正确声明。

## <a name="rule-description"></a>规则说明
 将平台调用方法访问非托管的代码与使用定义`Declare`中的关键字[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]或<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>。 目前，此规则查找针对平台调用目标有一个指针指向 OVERLAPPED 结构参数的 Win32 函数的方法声明和相应的托管的参数不是一个指向<xref:System.Threading.NativeOverlapped?displayProperty=fullName>结构。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复此规则的冲突，请正确声明在平台调用方法。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。

## <a name="example"></a>示例
 平台调用方法的规则冲突示例和满足该规则的以下示例所示。

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>请参阅
 [与非托管代码交互操作](/dotnet/framework/interop/index)