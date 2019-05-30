---
title: 使用旧版 API 提供的语言服务上下文 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cdb7c2ff3d759581569d0f3681ce1b2f9cef39c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334423"
---
# <a name="provide-a-language-service-context-by-using-the-legacy-api"></a>通过使用传统的 API 提供的语言服务上下文
有两个选项的语言服务以提供用户上下文中使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器： 提供文本标记的上下文，或提供所有的用户上下文。 下面概述了每个之间的差异。

 提供连接到您自己的编辑器的语言服务上下文的详细信息，请参阅[如何：为编辑器提供的上下文](../extensibility/how-to-provide-context-for-editors.md)。

## <a name="provide-text-marker-context-to-the-editor"></a>为编辑器提供文本标记上下文
 若要为编译器错误由文本标记中提供的上下文[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器，实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>接口。 在此方案中，语言服务仅当在光标位于文本标记上时提供上下文。 这允许提供到光标位置处关键字编辑器**动态帮助**窗口不具有任何属性。

## <a name="provide-all-user-context-to-the-editor"></a>为编辑器提供所有的用户上下文
 如果您要创建语言服务，并且使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器，然后，可以实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>接口来为你的语言服务提供的上下文。

 有关实现的`IVsLanguageContextProvider`，上下文包 （集合） 附加到编辑器，它是负责更新上下文包。 当**动态帮助**窗口调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A>接口对此上下文包在空闲时，上下文包查询更新的编辑器。 在编辑器然后通知语言服务，它应更新编辑器中，并将指针传递到上下文包。 这是通过调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>从编辑器到语言服务的方法。 到上下文包使用的指针，该语言服务可以现在添加和删除属性和关键字。 有关详细信息，请参阅 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>。

 有两种不同方式实现`IVsLanguageContextProvider`:

- 提供对上下文包关键字

   当在编辑器调用来更新上下文包时，传入适当的关键字和属性，然后返回`S_OK`。 此返回值指示要保留关键字和属性上下文而不会提供上下文包到光标位置处关键字的编辑器。

- 获取从光标位置处关键字的关键字

   当编辑器调用以更新上下文包时，相应的属性中传递，然后返回`E_FAIL`。 此返回值指示要保留你的特性中的上下文包，但更新上下文包使用的光标位置处关键字的编辑器。

  下图演示了如何实现的语言服务提供上下文`IVsLanguageContextProvider`。

  ![LangServiceImplementation2 图](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")语言服务上下文

  正如您在图中，可以看到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心文本编辑器具有上下文包连接到它。 此上下文包指向三个单独的子上下文包： 语言服务、 默认编辑器和文本标记。 语言服务和文本标记子上下文包包含特性和关键字为语言服务，如果<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>接口实现，以及文本标记如果<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>接口实现。 如果未实现这些接口之一，在编辑器对默认编辑器子上下文包中光标位置处关键字提供上下文。

## <a name="context-guidelines-for-editors-and-designers"></a>上下文为编辑器和设计器的指导原则
 设计器和编辑器必须提供的编辑器或设计器窗口的常规关键字。 这是，以使用户按下时，泛型类型，但相应，帮助主题将显示设计器或编辑器**F1**。 编辑器必须除此之外，提供当前光标位置处关键字或提供基于当前所选内容的关键术语。 这样做是为了确保指向或用户按下时，选择显示的文本或 UI 元素帮助主题**F1**。 设计器提供了设计器，如在窗体上按钮中选择的项的上下文。 编辑器和设计器还必须连接到语言服务中所述[旧版语言服务基础知识](../extensibility/internals/legacy-language-service-essentials.md)。