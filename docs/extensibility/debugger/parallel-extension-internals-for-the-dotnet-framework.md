---
title: .NET framework 并行扩展内幕 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0437363dd7d45b95a04a9e58edd45229f14b4c93
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925357"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>.NET Framework 的并行扩展内幕
本节介绍了内部类型、 方法和字段的类，可帮助您实现自定义.NET Framework 并行扩展调试器。

## <a name="in-this-section"></a>本节内容
 [Task 类](../../extensibility/debugger/task-class-internal-members.md)的内部数据成员进行了说明<xref:System.Threading.Tasks.Task?displayProperty=fullName>类。

 [TaskScheduler 类](../../extensibility/debugger/taskscheduler-class-internal-members.md)的内部数据成员进行了说明<xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>类。

 [ContingentProperties 类](../../extensibility/debugger/contingentproperties-class-internal-members.md)的内部数据成员进行了说明`System.Threading.Tasks.ContingentProperties`类。

 [AsyncTaskMethodBuilder 结构](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)介绍的内部成员<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>结构。

 [AsyncTaskMethodBuilder\<TResult > 结构](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)的内部成员进行了说明<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>结构。

 [AsyncVoidMethodBuilder 结构](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)介绍的内部成员<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>结构。

## <a name="see-also"></a>请参阅
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Visual Studio 调试器可扩展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [并行编程](/dotnet/standard/parallel-programming/index)