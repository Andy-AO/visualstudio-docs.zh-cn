---
title: 如何：添加、更新或删除 WCF 数据服务引用 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89a667e3254be8161d4defb54d524756a5eb02fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670007"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>如何：添加、更新或移除 WCF 数据服务引用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*服务引用*允许项目访问一个或多个 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 。 使用 " **添加服务引用** " 对话框可以在本地 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 、在本地网络或 Internet 上搜索当前解决方案。

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-a-service-reference"></a>添加服务引用

#### <a name="to-add-a-reference-to-an-external-service"></a>添加对外部服务的引用

1. 在 **解决方案资源管理器**中，右键单击要向其添加服务的项目的名称，然后单击 " **添加服务引用**"。

     此时将出现“添加服务引用”对话框****。

2. 在 " **地址** " 框中，输入服务的 URL，然后单击 " **开始** " 搜索服务。 如果服务实施用户名和密码安全，系统可能会提示你输入用户名和密码。

    > [!NOTE]
    > 应仅从受信任源引用服务。 从不受信任的源添加引用可能会危及安全性。

     你还可以从 "地址" 列表中选择 URL，该 **地址** 将存储找到了有效服务元数据的前15个 url。

     执行搜索时，将显示一个进度栏。 您可以随时通过单击 " **停止**" 来停止搜索。

3. 在 " **服务** " 列表中，展开要使用的服务的节点，然后选择实体集。

4. 在“命名空间”框中，输入要用于参考的命名空间****。

5. 单击“确定”将参考添加到项目中****。

     将生成服务客户端 (代理) ，并将描述服务的元数据添加到 app.config 文件中。

#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>在当前解决方案中添加对服务的引用

1. 在 **解决方案资源管理器**中，右键单击要向其添加服务的项目的名称，然后单击 " **添加服务引用**"。

     此时将出现“添加服务引用”对话框****。

2. 单击 " **发现**"。

     [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]当前解决方案中 (和 WCF 服务) 的所有服务都将添加到**服务**列表中。

3. 在 " **服务** " 列表中，展开要使用的服务的节点，然后选择实体集。

4. 在“命名空间”框中，输入要用于参考的命名空间****。

5. 单击“确定”将参考添加到项目中****。

     将生成服务客户端 (代理) ，并将描述服务的元数据添加到 app.config 文件中。

## <a name="updating-a-service-reference"></a>更新服务引用
 的实体数据模型 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 有时会发生更改。 发生这种情况时，必须更新服务引用。

#### <a name="to-update-a-service-reference"></a>更新服务引用

- 在 **解决方案资源管理器**中，右键单击服务引用，然后单击 " **更新服务引用**"。

     当引用从其原始位置更新时，将显示进度对话框，然后重新生成服务客户端以反映元数据中的任何更改。

## <a name="removing-a-service-reference"></a>删除服务引用
 如果不再使用服务引用，则可以将其从解决方案中删除。

#### <a name="to-remove-a-service-reference"></a>删除服务引用

- 在 **解决方案资源管理器**中，右键单击服务引用，然后单击 " **删除**"。

     将从解决方案中删除服务客户端，并将从 app.config 文件中删除描述该服务的元数据。

    > [!NOTE]
    > 引用服务引用的任何代码都必须手动删除。

## <a name="see-also"></a>另请参阅
 [在 Visual Studio 中 Windows Communication Foundation 服务和 WCF 数据服务](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
