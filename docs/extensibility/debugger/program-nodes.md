---
title: 程序节点 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93c2d82ca683e7fb771ff3a443eb54746d4bde29
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925255"
---
# <a name="program-nodes"></a>程序节点
在调试器体系结构中，*程序节点*:

- 是一个程序的轻型说明。

- 可以标识本身和它正在运行中的进程。 程序节点可以附加、 分离，并介绍创建它，调试引擎 (DE)，如果有的话。

- 为由[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)接口，通常由 DE 或端口。 程序节点添加到端口通过调用[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)。 当程序节点添加到端口后时，它被添加到包含此程序节点表示程序进程。

  调试会话已启动一段时间，具体取决于调试包的实现后程序节点用于创建相应的程序。 在其程序中查询一个过程，将枚举程序，另一个用于每个程序节点。

  程序附加到之前，IDE 将要求仅该程序的轻型的描述。 可以从程序节点中获取此信息。 一旦程序附加到，则 IDE 将显示更多详细的信息，例如，在程序中运行的所有线程的列表。 从程序自身获取此信息。

## <a name="see-also"></a>请参阅
- [程序](../../extensibility/debugger/programs.md)
- [进程](../../extensibility/debugger/processes.md)
- [调试引擎](../../extensibility/debugger/debug-engine.md)
- [调试器概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)