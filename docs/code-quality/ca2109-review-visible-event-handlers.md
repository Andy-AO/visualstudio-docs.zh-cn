---
title: CA2109:检查可见的事件处理程序
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de5ab1fac368f1da1ceea39df19b198a22d999c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808284"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109:检查可见的事件处理程序

|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|类别|Microsoft.Security|
|是否重大更改|重大|

## <a name="cause"></a>原因
 检测到公共事件处理方法或受保护事件处理方法。

## <a name="rule-description"></a>规则说明
 外部可见的事件处理方法提供了需要查看安全问题。

不要公开事件处理方法，除非绝对必要。 可以向任何事件添加一个事件处理程序委托类型，用于调用公开的方法，只要处理程序和事件的签名匹配。 事件可能会引起的任何代码，并频繁地引发的高度受信任的系统代码以响应用户操作，例如单击按钮。 将安全检查添加到的事件处理方法不会阻止代码注册事件处理程序调用的方法。

 要求不能可靠地保护由事件处理程序调用的方法。 安全请求有助于防止代码免受不受信任调用方通过检查调用堆栈上的调用方。 事件处理程序的方法在运行时，将事件处理程序添加到事件的代码不一定存在调用堆栈上。 因此，调用堆栈可能具有仅高度受信任的调用方调用事件处理程序方法时。 这将导致发出的事件处理程序方法才能成功请求。 此外，调用此方法，则可能会添加要求的权限。 出于这些原因，仅可以查看的事件处理方法后评估不修复该规则的冲突的风险。 当查看你的代码时，请考虑以下问题：

- 事件处理程序是否执行危险或可被利用，如断言权限或禁止显示非托管的代码权限的任何操作？

- 什么是与你的代码的安全威胁，因为可以随时与高度仅运行受信任调用方在堆栈上？

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复此规则的冲突，请检查该方法并评估以下：

- 您可以将事件处理方法非公共？

- 是否可以移动的事件处理程序的所有危险多功能？

- 如果施加的安全要求，这可以以某种其他方式？

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 禁止显示此规则警告在仔细检查安全性后，才以确保你的代码不会构成安全威胁。

## <a name="example"></a>示例
 下面的代码演示可被恶意代码误用的事件处理方法。

 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]

## <a name="see-also"></a>请参阅

- <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>
- <xref:System.EventArgs?displayProperty=fullName>