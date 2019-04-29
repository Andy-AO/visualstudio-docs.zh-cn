---
title: CA2122:不要使用链接请求间接公开方法
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8239b27cd92f66ae8f74ddb1accd95535bf56f93
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542332"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122:不要使用链接请求间接公开方法

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|类别|Microsoft.Security|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因
 公共或受保护成员具有[链接要求](/dotnet/framework/misc/link-demands)，并由不执行任何安全检查的成员。

## <a name="rule-description"></a>规则说明
 链接请求仅检查直接调用方的权限。 如果成员`X`使其调用方，并调用代码受链接要求，调用方没有所需的权限可以使用的安全请求`X`来访问受保护的成员。

## <a name="how-to-fix-violations"></a>如何解决冲突
 添加安全[数据和建模](/dotnet/framework/data/index)或将需求链接到该成员，以便它不再提供对受链接要求保护的成员的不安全的访问。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 若要安全地禁止显示此规则的警告，必须确保你的代码不会授予其调用方访问操作或可以以破坏方式使用的资源。

## <a name="example-1"></a>示例 1
 以下示例演示一个库，它违反了此规则和演示库的漏洞的应用程序。 示例库提供一起违反规则的两种方法。 `EnvironmentSetting`方法受链接要求无限制地访问环境变量。 `DomainInformation`方法发出安全请求其调用方的调用之前`EnvironmentSetting`。

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>示例 2
 下面的应用程序调用的不安全的库成员。

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

该示例产生下面的输出：

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>请参阅

- [安全编码准则](/dotnet/standard/security/secure-coding-guidelines)
- [链接需求](/dotnet/framework/misc/link-demands)
- [数据和建模](/dotnet/framework/data/index)