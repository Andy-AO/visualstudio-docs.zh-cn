---
title: CA2147：透明方法不能使用安全断言 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 45639afc9946aa43df121a5a1881174371413c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546375"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147:透明方法不得使用安全断言
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|项|值|
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|类别|Microsoft.Security|
|是否重大更改|重大|

## <a name="cause"></a>原因
 被标记为的代码 <xref:System.Security.SecurityTransparentAttribute> 未被授予足够的权限进行断言。

## <a name="rule-description"></a>规则描述
 此规则分析程序集中的所有方法和类型，该程序集为100% 透明或混合透明/关键，并标志的任何声明性或命令性用法 <xref:System.Security.CodeAccessPermission.Assert%2A> 。

 在运行时，对从透明代码进行的任何调用 <xref:System.Security.CodeAccessPermission.Assert%2A> 都将导致 <xref:System.InvalidOperationException> 引发。 这种情况可能发生在100% 透明程序集，也可能出现在混合透明/关键程序集中，其中方法或类型声明为透明，但包含声明性或命令式断言。

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]2.0 引入了一个名为 "*透明度*" 的特性。 各个方法、字段、接口、类和类型可以是透明的或关键的。

 不允许透明代码提升安全权限。 因此，任何授予或要求的权限都将自动通过代码传递给调用方或主机应用程序域。 提升的示例包括断言、Linkdemand、SuppressUnmanagedCode 和 `unsafe` 代码。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要解决此问题，请将调用断言的代码标记为 <xref:System.Security.SecurityCriticalAttribute> ，或删除断言。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 请勿禁止显示此规则的消息。

## <a name="example"></a>示例
 如果 `SecurityTestClass` 是透明的，则当该方法引发时，此代码将失败 `Assert` <xref:System.InvalidOperationException> 。

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>示例
 其中一种方法是在下面的示例中查看 SecurityTransparentMethod 方法，如果该方法被认为是安全的，则将 SecurityTransparentMethod 标记为安全关键，这要求在方法上执行详细的、完整和无错误的安全审核，以及在断言下的方法中发生的任何调用。

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 另一种方法是从代码中删除断言，并让任何后续的文件 i/o 权限要求在 SecurityTransparentMethod 到调用方之前流动。 这将启用安全检查。 在这种情况下，不需要进行安全审核，因为权限要求会流向调用方和/或应用程序域。 权限要求通过安全策略、宿主环境和代码源权限授予进行严格控制。

## <a name="see-also"></a>另请参阅
 [安全警告](../code-quality/security-warnings.md)
