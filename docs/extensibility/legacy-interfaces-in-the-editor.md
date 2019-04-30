---
title: 在编辑器中的旧接口 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 044bf36845be70290291b79dee255c452f56f0a0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907484"
---
# <a name="legacy-interfaces-in-the-editor"></a>在编辑器中的旧接口
可以从旧式界面访问 Visual Studio 编辑器。 Visual Studio SDK 包括适配器称为*填充程序*，它实现了这些接口，以便与新编辑器。 不过，我们建议你更新旧代码，以使用新编辑器 API。 你的代码将更好地执行，可以使用 Windows Presentation Foundation (WPF) 和 Managed Extensibility Framework (MEF) 等新技术。

## <a name="related-topics"></a>相关主题

| 标题 | 描述 |
| - | - |
| [调整到编辑器的旧代码](../extensibility/adapting-legacy-code-to-the-editor.md) | 介绍如何适应您的代码与新编辑器。 |
| [新的或更改行为与编辑器适配器](../extensibility/new-or-changed-behavior-with-editor-adapters.md) | 介绍编辑器适配器的行为方式不同于早期版本的编辑器。 |
| [在核心编辑器](../extensibility/inside-the-core-editor.md) | 介绍编辑器的早期版本的不同组件。 |
| [通过使用传统的 API 实例核心编辑器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md) | 介绍如何使用传统的 API 来实例化核心编辑器。 |
| [编辑器工厂](../extensibility/editor-factories.md) | 介绍如何使用编辑器工厂与传统的 API。 |
| [如何：注册编辑器文件类型](../extensibility/how-to-register-editor-file-types.md) | 介绍如何将文件扩展名为链接到你的编辑器。 |
| [演练：创建编辑器的一个核心并注册编辑器文件类型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md) | 介绍如何创建编辑器的一个核心并链接到该文件扩展名。 |
| [如何：为编辑器提供的上下文](../extensibility/how-to-provide-context-for-editors.md) | 介绍如何为你的编辑器提供的上下文。 |
| [语言服务和核心编辑器](../extensibility/language-services-and-the-core-editor.md) | 介绍了语言服务和编辑器之间的交互。 |
| [通过使用传统的 API 访问的文本缓冲区](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md) | 介绍如何使用传统的 API 访问的文本缓冲区。 |
| [通过使用传统的 API 访问文本视图](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) | 介绍如何使用传统的 API 访问文本视图。 |
| [使用传统的 API 自定义代码窗口](../extensibility/customizing-code-windows-by-using-the-legacy-api.md) | 介绍如何使用传统的 API 自定义代码窗口。 |
| [通过使用传统的 API 访问文本层](../extensibility/accessing-text-layers-by-using-the-legacy-api.md) | 介绍如何使用传统的 API 访问不同层的文本。 |
| [文本标记中使用传统的 API](../extensibility/using-text-markers-with-the-legacy-api.md) | 介绍如何使用传统的 API 添加文本标记。 |
| [使用传统的 API 自定义编辑器控件和菜单](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md) | 介绍如何使用传统的 API 自定义编辑器控件。 |
| [管理撤消和重做通过使用传统的 API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md) | 介绍如何管理撤消和重做通过使用传统的 API。 |
| [如何：实现查找和替换机制](../extensibility/how-to-implement-the-find-and-replace-mechanism.md) | 介绍如何管理查找和替换为通过使用传统的 API。 |
| [如何：禁止显示文件更改通知](../extensibility/how-to-suppress-file-change-notifications.md) | 介绍如何通过使用传统的 API 来禁止显示文件更改通知。 |
| [创建自定义编辑器和设计器](../extensibility/creating-custom-editors-and-designers.md) | 说明如何创建自定义编辑器和设计器。 |
| [开发旧版语言服务](../extensibility/internals/developing-a-legacy-language-service.md) | 提供的功能提供了对自定义功能的文档的链接[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]通过添加对语言服务支持的核心编辑器。 |
| [使用字体和颜色](../extensibility/using-fonts-and-colors.md) | 介绍如何使用旧式界面字体和颜色。 |
