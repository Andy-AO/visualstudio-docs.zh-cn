---
title: CA2142：不应通过 Linkdemand 保护透明代码 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa6bd9dcacc5fb863199c740a71c824f14739052
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546427"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142:不应使用 LinkDemand 保护透明代码
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|项|值|
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|类别|Microsoft.Security|
|是否重大更改|重大|

## <a name="cause"></a>原因
 透明方法需要 <xref:System.Security.Permissions.SecurityAction> 或其他安全要求。

## <a name="rule-description"></a>规则描述
 对于需要 LinkDemand 来访问它们的透明方法，将会引发此规则。 安全透明代码不应负责验证某个操作的安全，因此不应要求权限。 因为透明方法应为安全特定方法，所以它们不应进行任何安全决策。 此外，保证安全决策的安全关键代码不应依赖透明代码来进行此类决定。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复与此规则的冲突，请删除透明方法的链接要求，或在 <xref:System.Security.SecuritySafeCriticalAttribute> 执行安全检查（如安全要求）时使用特性标记该方法。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。

## <a name="example"></a>示例
 在下面的示例中，规则在方法上触发，因为方法是透明的，并标记有包含的 LinkDemand <xref:System.Security.PermissionSet> <xref:System.Security.Permissions.SecurityAction> 。

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2142.transparentmethodsshouldnotbeprotectedwithlinkdemands/cs/ca2142 -transparentmethodsshouldnotbeprotectedwithlinkdemands.cs#1)]

 不禁止显示此规则发出的警告。
