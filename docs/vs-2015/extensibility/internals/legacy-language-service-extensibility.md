---
title: 旧版语言服务扩展性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 43
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9346311aac4bc5833005423e90c2eb92faddcb84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194979"
---
# <a name="legacy-language-service-extensibility"></a>旧版语言服务扩展性
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

语言服务为在 IDE 中编辑源代码提供特定于语言的支持。  
  
 旧版语言服务是作为 VSPackage 的一部分实现的，但实现语言服务功能的更新方法是使用 MEF 扩展。 若要了解有关实现语言服务的新方法的详细信息，请参阅 [编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)。  
  
 本部分讨论旧版语言服务的结构和实现。  
  
## <a name="in-this-section"></a>本节内容  
 [迁移旧版语言服务](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 说明如何将语言服务从 Visual Studio 2008 更新到最新版本。  
  
 [旧版语言服务基础知识](../../extensibility/internals/legacy-language-service-essentials.md)  
 提供有关如何开发语言服务以将编程语言集成到 Visual Studio 的重要信息。  
  
 [开发旧版语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)  
 提供指向可帮助你创建语言服务的主题的链接。  
  
 [在旧版语言服务中进行语法着色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 提供有关在语言服务中支持语法突出显示的信息。  
  
 [实现旧版语言服务](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 提供有关如何使用托管包框架 (MPF) 在托管代码中实现全功能语言服务的信息。  
  
 [支持符号浏览工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 介绍可用于在 IDE 中浏览符号的树视图的库和工具。  
  
## <a name="related-sections"></a>相关章节  
 [编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)  
 提供 Visual Studio 编辑器的概述。  
  
 [用于调试的语言服务支持](../../extensibility/internals/language-service-support-for-debugging.md)  
 提供有关和 Visual Studio 调试 SDK 的链接，其中包含创建和自定义用于调试程序的调试器组件所需的信息。
