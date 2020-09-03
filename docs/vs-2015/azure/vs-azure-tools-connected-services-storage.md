---
title: 使用连接的服务添加 Azure 存储
description: 使用 Visual Studio 的“添加连接服务”对话框将 Azure 存储添加到应用
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 3acb009d27a9fa47f890235f6957d1f29ed2f4a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916698"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>使用 Visual Studio 连接服务添加 Azure 存储
在 Visual Studio 中，通过使用“添加连接服务”**** 对话框可将以下任何服务连接到 Azure 存储：

- C# 云服务
- .NET 后端移动服务
- ASP.NET 网站或服务
- ASP.NET Core 服务
- Azure WebJob 服务

连接服务功能可将所有需要的引用和连接代码添加到项目，并相应地修改配置文件。

完成后，“添加连接服务”**** 对话框会自动显示文档，其中详细介绍开始使用 blob 存储、队列和表所需的步骤。

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>使用“连接服务”对话框连接到 Azure 存储
1. 在 Visual Studio 中打开项目

1. 在“解决方案资源管理器”**** 中，右键单击“连接服务”**** 节点，并在上下文菜单中选择“添加连接服务”****。

    ![添加 Azure 连接服务](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. 在“连接服务”**** 页面中，选择“Azure 存储的云存储”****。

    ![添加 Azure 存储](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. 在“Azure 存储”**** 对话框中，选择一个现有的存储帐户，并选择“添加”****。

    若要要创建存储帐户，请转到下一步。 否则，请跳到步骤 6。

    ![将现有存储帐户添加到项目](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. 创建存储帐户：

   1. 选择对话框底部的“创建新存储帐户”****。

   1. 填写“创建存储帐户”**** 对话框，并选择“创建”****。

       ![新的 Azure 存储帐户](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. 显示“Azure 存储”**** 对话框时，新的存储帐户会显示在列表中。 在列表中选择新存储帐户，并选择“添加”****。

1. 该存储连接服务会显示在项目的“服务引用”**** 节点下。

## <a name="how-your-project-is-modified"></a>项目的修改情况
完成该对话框后，Visual Studio 将添加引用并修改特定配置文件。 具体更改情况取决于项目类型：

- ASP.NET 项目 - [完成的操作 – ASP.NET 项目](/azure/visual-studio/vs-storage-aspnet-getting-started-blobs)
- ASP.NET Core 项目 - [完成的操作 – ASP.NET 5 项目](/azure/visual-studio/vs-storage-aspnet5-getting-started-blobs)
- 云服务项目（Web 角色和辅助角色）- [完成的操作 – 云服务项目](/azure/visual-studio/vs-storage-cloud-services-getting-started-blobs)
- WebJob 项目 - [完成的操作 – WebJob 项目](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>后续步骤
- [MSDN 论坛：Azure 存储](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Microsoft Azure 存储团队博客](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Azure 存储文档](/azure/storage/)
