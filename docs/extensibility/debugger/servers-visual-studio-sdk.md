---
title: 服务器 (Visual Studio SDK) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56ec28d0d9202bfd72d31e95c53038dd1fa475e9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912992"
---
# <a name="servers-visual-studio-sdk"></a>服务器 (Visual Studio SDK)
在调试器体系结构中， *server*:

- 是一个容器的端口和端口提供程序和与会话调试管理器 (SDM) 和调试引擎进行通信的端口和端口提供程序。

- 可以按名称、 标识本身和枚举其端口和端口提供程序。

- 为由[IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)接口，仅实现由 Visual Studio （在 Visual Studio 运行的每个实例的服务器的一个实例）。

## <a name="see-also"></a>请参阅
- [端口](../../extensibility/debugger/ports.md)
- [端口提供程序](../../extensibility/debugger/port-suppliers.md)
- [调试器概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)