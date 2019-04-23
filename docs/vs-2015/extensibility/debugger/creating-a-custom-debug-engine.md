---
title: 创建自定义调试引擎 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 829e484ffe4968cdb89ff04e4e7f145decd07c9c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111514"
---
# <a name="creating-a-custom-debug-engine"></a>创建自定义调试引擎
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

调试引擎 (DE) 是允许调试特定运行时体系结构的组件。 通常是只有一个 DE 实现每个运行时环境。  
  
> [!NOTE]
>  虽然有单独的 DE 实现 TRANSACT-SQL 和 JScript，VBScript 和 JScript 共享单个 DE。  
  
 部署适用于解释器或操作系统提供执行控制、 断点、 和表达式计算等调试服务。 这些服务通过 DE 接口实现，并可能会导致调试程序对不同的操作模式之间的转换。 有关详细信息，请参阅[操作模式](../../extensibility/debugger/operational-modes.md)。  
  
 创建部署包含以下步骤：  
  
1. 使用 Visual Studio 注册 DE  
  
2. 启用要进行调试的程序  
  
3. 执行控件和状态评估  
  
4. 发送事件  
  
5. 终止和分离  
  
## <a name="in-this-section"></a>本节内容  
 [注册自定义调试引擎](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 介绍使用 Visual Studio 注册调试引擎，可以使用它所需的步骤。  
  
 [启用要进行调试的程序](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 介绍了你 DE 可调试的程序之前，必须首先启动 DE 或将其附加到现有的程序。  
  
 [执行控件和状态计算](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 讨论为什么要调试的应用程序要求实现执行控制功能。  
  
 [发送事件](../../extensibility/debugger/sending-events.md)  
 描述调试器和 DE 之间作为事件模型基于 DCOM 的通信。  
  
 [终止和分离](../../extensibility/debugger/termination-and-detaching.md)  
 介绍如何实现正常终止，这不意味着任何断点、 异常、 运行时错误或要进行调试的应用程序中的无限循环。  
  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)  
 记录调试会话中发生的事件的调用顺序。  
  
 [如何：调试自定义调试引擎](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 说明如何调试自定义部署。  
  
## <a name="see-also"></a>请参阅  
 [Visual Studio 调试器可扩展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
