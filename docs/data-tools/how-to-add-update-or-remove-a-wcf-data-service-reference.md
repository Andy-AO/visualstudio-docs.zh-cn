---
title: 如何：添加、更新或删除 WCF 数据服务引用
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4591c6b794905eb0b8742292c752762cdea991e0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099528"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>如何：添加、更新或删除 WCF 数据服务引用
一个*服务参考*使得访问一个或多个项目[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]。 使用**添加服务引用**对话框可以搜索[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]在当前解决方案中，本地、 在本地网络，或在 Internet 上。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>添加服务引用

### <a name="to-add-a-reference-to-an-external-service"></a>若要添加对外部服务的引用

1. 在中**解决方案资源管理器**，右键单击你想要添加该服务，然后单击的项目名称**添加服务引用**。

     **添加服务引用**对话框随即出现。

2. 在中**地址**框中，输入该服务的 URL，然后单击**转**来搜索服务。 如果该服务实现了用户名称和密码安全性，您可能会提示输入用户名和密码。

    > [!NOTE]
    >  应仅从受信任源引用服务。 从不受信任的源添加引用可能会危及安全性。

     您还可以选择从 URL**地址**列表，其中存储了在其中找到有效的服务元数据的前 15 个。

     执行搜索时，将显示一个进度栏。 可以通过单击停止搜索在任何时候**停止**。

3. 在中**Services**列表中，展开你想要使用，并选择一个实体集的服务的节点。

4. 在中**Namespace**框中，输入你想要用于参考的命名空间。

5. 单击**确定**添加到项目引用。

     生成服务客户端 （代理），并描述该服务的元数据添加到*app.config*文件。

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>若要在当前解决方案中添加对服务的引用

1. 在中**解决方案资源管理器**，右键单击你想要添加该服务，然后单击的项目名称**添加服务引用**。

    **添加服务引用**对话框随即出现。

2. 单击**发现**。

    所有服务 (同时[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]和 WCF 服务) 当前解决方案中添加到**Services**列表。

3. 在中**Services**列表中，展开你想要使用，并选择一个实体集的服务的节点。

4. 在中**Namespace**框中，输入你想要用于参考的命名空间。

5. 单击**确定**添加到项目引用。

    生成服务客户端 （代理），并描述该服务的元数据添加到*app.config*文件。

## <a name="update-a-service-reference"></a>更新服务引用
 实体数据模型的[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]有时会更改。 在此情况下，必须更新服务引用。

### <a name="to-update-a-service-reference"></a>若要更新服务引用

- 在中**解决方案资源管理器**，右键单击服务引用，然后单击**更新服务引用**。

     从其原始位置更新的引用并重新生成服务客户端以反映元数据中的任何更改时，将显示一个进度对话框。

## <a name="remove-a-service-reference"></a>删除服务引用
 如果不再使用的服务引用，则可以从你的解决方案中将其删除。

### <a name="to-remove-a-service-reference"></a>若要删除服务引用

- 在中**解决方案资源管理器**，右键单击服务引用，然后单击**删除**。

     服务客户端将删除该解决方案，并描述该服务的元数据将不再从*app.config*文件。

    > [!NOTE]
    >  必须手动删除引用的服务引用的任何代码。

## <a name="see-also"></a>请参阅

- [Visual Studio 中的 Windows Communication Foundation 服务和 WCF 数据服务](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)