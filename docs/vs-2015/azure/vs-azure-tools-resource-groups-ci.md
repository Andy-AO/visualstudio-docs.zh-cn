---
title: 使用 Azure 资源组项目在 Azure DevOps Services 中持续集成 | Microsoft Docs
description: 介绍如何在 Visual Studio 中使用 Azure 资源组部署项目在 Azure DevOps Services 中设置持续集成。
author: mlearned
manager: jillfra
ms.assetid: b81c172a-be87-4adc-861e-d20b94be9e38
ms.topic: article
ms.workload: azure-vs
ms.date: 08/01/2016
ms.author: mlearned
ms.openlocfilehash: 0b95b34fe4c66590d3475368c837092f58aad05f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429435"
---
# <a name="continuous-integration-in-azure-devops-services-using-azure-resource-group-deployment-projects"></a>使用 Azure 资源组部署项目在 Azure DevOps Services 中持续集成

若要部署 Azure 模板，请执行各个阶段的任务：生成、测试、复制到 Azure（也称为“暂存”）和部署模板。 可通过两种不同的方法将模板部署到 Azure DevOps Services。 两种方法产生的结果相同，因此请选择最符合工作流的方法。

1. 在运行 PowerShell 脚本的生成管道（包含在 Azure 资源组部署项目 Deploy-AzureResourceGroup.ps1 中）中添加一个步骤。 该脚本将复制项目，然后部署模板。
2. 添加多个 Azure DevOps Services 生成步骤，每个步骤执行一个阶段任务。

本文演示了这两个选项。 第一个选项的优点是，在 Visual Studio 中使用开发人员所用的同一脚本，并且在整个生命周期中提供一致性。 第二个选项为内置脚本提供一个便捷替代方式。 两个过程都假设已经在 Azure DevOps Services 中签入 Visual Studio 部署项目。

## <a name="copy-artifacts-to-azure"></a>将项目复制到 Azure
无论方案如何，如果具有模板部署所需的任何项目，必须向 Azure 资源管理器授予这些项目的访问权限。 这些项目可以包括如下所述的文件：

* 嵌套模板
* 配置脚本和 DSC 脚本
* 应用程序二进制文件

### <a name="nested-templates-and-configuration-scripts"></a>嵌套模板和配置脚本
使用 Visual Studio 提供的模板（或以 Visual Studio 代码段生成的模板）时，PowerShell 脚本不但会暂存项目，而且会参数化用于不同部署的资源的 URI。 脚本会将项目复制到 Azure 中的安全容器，为该容器创建 SaS 令牌，然后将该信息传递到模板部署。 若要了解有关嵌套模板的详细信息，请参阅[创建模板部署](https://msdn.microsoft.com/library/azure/dn790564.aspx)。  在 Azure DevOps Services 中使用任务时，必须为模板部署选择相应任务，并在必要时将暂存步骤中的参数值传递到模板部署。

## <a name="set-up-continuous-deployment-in-azure-pipelines"></a>在 Azure Pipelines 中设置持续部署
若要在 Azure Pipelines 中调用 PowerShell 脚本，需更新生成管道。 简而言之，请执行以下步骤：

1. 编辑生成管道。
2. 在 Azure Pipelines 中设置 Azure 授权。
3. 添加一个引用 Azure 资源组部署项目中 PowerShell 脚本的 Azure PowerShell 生成步骤。
4. 设置 *-ArtifactsStagingDirectory* 参数的值，以使用 Azure Pipelines 中生成的项目。

### <a name="detailed-walkthrough-for-option-1"></a>选项 1 详细演练
以下过程详述了完成下述操作所需的步骤：使用在项目中运行 PowerShell 脚本的单个任务，在 Azure DevOps Services 中配置持续部署。

1. 编辑 Azure DevOps Services 生成管道并添加 Azure PowerShell 生成步骤。 在“生成管道”类别下选择生成管道，然后选择“编辑”链接。

   ![编辑生成管道](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough1.png)
2. 将新的“Azure PowerShell”生成步骤添加到生成管道，然后选择“添加生成步骤...” 按钮。

   ![添加生成步骤](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough2.png)
3. 选择“部署任务”类别，选择“Azure PowerShell”任务，并选择其“添加”按钮。

   ![添加任务](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough3.png)
4. 选择“Azure PowerShell”生成步骤，并填充其值。

   1. 如果已将 Azure 服务终结点添加到 Azure DevOps Services，请在“Azure 订阅”下拉列表框中选择订阅，然后跳到下一部分。

      如果 Azure DevOps Services 中没有 Azure 服务终结点，则需添加一个。 本小节将引导完成整个过程。 如果 Azure 帐户使用 Microsoft 帐户（例如 Hotmail），则必须执行以下步骤以获取服务主体身份验证。

   2. 选择“Azure 订阅”下拉列表框旁边的“管理”链接。

      ![管理 Azure 订阅](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough4.png)
   3. 在“新建服务终结点”下拉列表框中选择“Azure”。

      ![新的服务终结点](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough5.png)
   4. 在“添加 Azure 订阅”对话框中，选择“服务主体”选项。

      ![服务主体选项](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough6.png)
   5. 向“添加 Azure 订阅”对话框添加 Azure 订阅信息。 需要提供以下项：

      * 订阅 ID
      * 订阅名称
      * 服务主体 ID
      * 服务主体密钥
      * 租户 ID
   6. 向“订阅”名称框添加所选的名称。 此值稍后会在 Azure DevOps Services 中“Azure 订阅”的下拉列表内显示。

   7. 如果不知道自己的 Azure 订阅 ID，可以使用以下命令之一来检索它。

      对于 Azure PowerShell 脚本，请使用：

      `Get-AzureRmSubscription`

      对于 Azure CLI，请使用：

      `azure account show`
   8. 若要获取服务主体 ID、服务主体密钥和租户 ID，请遵循[使用门户创建 Active Directory 应用程序和服务主体](/azure/azure-resource-manager/resource-group-create-service-principal-portal)或[通过 Azure 资源管理器对服务主体进行身份验证](/azure/azure-resource-manager/resource-group-authenticate-service-principal)中的过程。
   9. 向“添加 Azure 订阅”对话框添加服务主体 ID、服务主体密钥和租户 ID 值，并选择“确定”按钮。

      现在，已获得了用于运行 Azure PowerShell 脚本的有效服务主体。
5. 编辑生成管道并选择 **Azure PowerShell** 生成步骤。 在“Azue 订阅”下拉列表框中选择订阅。 （如果订阅未出现，请选择“管理”链接旁边的“刷新”按钮。）

   ![安装 Azure PowerShell 生成任务](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough9.png)
6. 提供 Deploy-AzureResourceGroup.ps1 PowerShell 脚本的路径。 为此，请选择“脚本路径”框旁边的省略号 (…) 按钮，导航到项目的 **Scripts** 文件夹中的 Deploy-AzureResourceGroup.ps1 PowerShell 脚本，选择该脚本，并选择“确定”按钮。

   ![选择脚本的路径](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough10.png)
7. 选择该脚本后，更新脚本的路径，以便从 Build.StagingDirectory（与 *ArtifactsLocation* 设置到的目录相同）运行脚本。 可以通过在脚本路径的开头添加“$(Build.StagingDirectory)/”来执行此操作。

    ![编辑脚本的路径](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough11b.png)
8. 在“脚本参数”框中输入以下参数（在一行中）。 在 Visual Studio 中运行脚本时，可以在“输出”窗口中看到 VS 如何使用参数。 在生成步骤中设置参数值时，可使用此设置作为起点。

   | 参数 | 说明 |
   | --- | --- |
   | -ResourceGroupLocation |资源组所在的地理位置值，例如 **eastus** 或 **'East US'**。 （如果名称中有空格，请添加单引号。）有关详细信息，请参阅 [Azure 区域](https://azure.microsoft.com/regions/)。 |
   | -ResourceGroupName |此部署使用的资源组名称。 |
   | -UploadArtifacts |如果提供此参数，将指定需要从本地系统上传到 Azure 的项目。 仅当模板部署需要使用 PowerShell 脚本暂存其他项目（例如配置脚本或嵌套模板）时，才需要设置此开关。 |
   | -StorageAccountName |用于暂存此部署的项目的存储帐户名称。 仅当暂存用于部署的项目时，才使用此参数。 当此参数已提供时，如果在执行以前的部署期间脚本尚未创建一个存储帐户，将创建新的存储帐户。 如果已指定该参数，则存储帐户必须已经存在。 |
   | -StorageAccountResourceGroupName |与存储帐户关联的资源组名称。 仅在为 StorageAccountName 参数提供值时，才需要此参数。 |
   | -TemplateFile |Azure 资源组部署项目中的模板文件路径。 为了提高灵活性，请为此参数使用相对于 PowerShell 脚本位置的路径，而不要使用绝对路径。 |
   | -TemplateParametersFile |Azure 资源组部署项目中的参数文件路径。 为了提高灵活性，请为此参数使用相对于 PowerShell 脚本位置的路径，而不要使用绝对路径。 |
   | -ArtifactStagingDirectory |此参数使 PowerShell 脚本能够知道应从哪个文件夹中复制项目的二进制文件。 此值将覆盖 PowerShell 脚本使用的默认值。 为了方便 Azure DevOps Services 使用，请将该值设为 -ArtifactStagingDirectory $(Build.StagingDirectory) |

   下面是脚本参数示例（换行是为了便于阅读）：

   ```
   -ResourceGroupName 'MyGroup' -ResourceGroupLocation 'eastus' -TemplateFile '..\templates\azuredeploy.json'
   -TemplateParametersFile '..\templates\azuredeploy.parameters.json' -UploadArtifacts -StorageAccountName 'mystorageacct'
   –StorageAccountResourceGroupName 'Default-Storage-EastUS' -ArtifactStagingDirectory '$(Build.StagingDirectory)'
   ```

   完成之后，“脚本参数”框应类似于以下列表：

   ![脚本参数](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough12.png)
9. 将所有必需的项添加 Azure PowerShell 生成步骤之后，请选择“队列”生成按钮来生成项目。 “生成”屏幕会显示 PowerShell 脚本的输出。

### <a name="detailed-walkthrough-for-option-2"></a>选项 2 详细演练
以下过程演练使用内置任务在 Azure DevOps Services 中配置持续部署的必要步骤。

1. 编辑 Azure DevOps Services 生成管道，添加两个新的生成步骤。 在“生成定义”类别下选择生成管道，然后选择“编辑”链接。

   ![编辑生成定义](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough13.png)
2. 使用“添加生成步骤...”，将新的生成步骤添加到生成管道 按钮。

   ![添加生成步骤](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough14.png)
3. 依次选择“部署任务”类别、“Azure 文件复制”任务，并选择其“添加”按钮。

   ![添加 Azure 文件复制任务](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough15.png)
4. 选择“Azure 资源组部署”任务、选择其“添加”按钮，并**关闭**“任务目录”。

   ![添加 Azure 资源组部署任务](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough16.png)
5. 选择“Azure 文件复制”任务，并填充其值。

   如果已将 Azure 服务终结点添加到 Azure DevOps Services，请在“Azure 订阅”下拉列表框中选择订阅。 如果没有订阅，请参阅[选项 1](#detailed-walkthrough-for-option-1)，了解如何在 Azure DevOps Services 中设置订阅。

   * 源 - 输入 **$(Build.StagingDirectory)**
   * Azure 连接类型 - 选择“Azure 资源管理器”
   * Azure RM 订阅 - 针对存储帐户选择要在“Azure 订阅”下拉列表框中使用的订阅。 如果订阅未出现，请选择“管理”链接旁边的“刷新”按钮。
   * 目标类型 - 选择“Azure Blob”
   * RM 存储帐户 - 选择要用于暂存项目的存储帐户
   * 容器名称 - 输入要用于暂存的容器名称，它可以是任何有效的容器名称，但请使用一个专用于此生成管道的名称

   对于输出值：

   * 存储容器 URI - 输入 **artifactsLocation**
   * 存储容器 SAS 令牌 - 输入 **artifactsLocationSasToken**

   ![配置 Azure 文件复制任务](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough17.png)
6. 选择“Azure 资源组部署”生成步骤，并填充其值。

   * Azure 连接类型 - 选择“Azure 资源管理器”
   * Azure RM 订阅 - 在“Azure 订阅”下拉列表框中选择用于部署的订阅。 这通常是上一步中使用的同一订阅
   * 操作 - 选择“创建或更新资源组”
   * 资源组 - 选择资源组或为部署选择新资源组的名称
   * 位置 - 选择资源组的位置
   * 模板 - 输入要部署的模板路径和名称，并在前面附加 **$(Build.StagingDirectory)**，例如：**$(Build.StagingDirectory/DSC-CI/azuredeploy.json)**
   * 模板参数 - 输入要使用的参数路径和名称，并在前面附加 **$(Build.StagingDirectory)**，例如：**$(Build.StagingDirectory/DSC-CI/azuredeploy.parameters.json)**
   * 替代模板参数 - 输入或复制并粘贴以下代码：

     ```
     -_artifactsLocation $(artifactsLocation) -_artifactsLocationSasToken (ConvertTo-SecureString -String "$(artifactsLocationSasToken)" -AsPlainText -Force)
     ```

     ![配置 Azure 资源组部署任务](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough18.png)
7. 在添加所有必需项之后，保存生成管道，并选择顶部的“使新生成入队”。

## <a name="next-steps"></a>后续步骤

若要了解有关 Azure 资源管理器和 Azure 资源组的详细信息，请阅读 [Azure 资源管理器概述](/azure/azure-resource-manager/resource-group-overview)。