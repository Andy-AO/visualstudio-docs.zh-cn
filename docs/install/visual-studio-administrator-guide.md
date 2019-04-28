---
title: Visual Studio 管理员指南
titleSuffix: ''
description: 详细了解如何在企业环境中部署 Visual Studio。
ms.date: 04/02/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e228ca06aee6644b57782b30a1a9b02b17435f9d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951342"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio 管理员指南

在企业环境中，系统管理员通常会从网络共享或通过使用系统管理软件向最终用户部署安装。 为了支持企业部署，我们精心设计了 Visual Studio 安装程序引擎，以便系统管理员可以创建网络安装位置、预配置安装默认值、在安装过程中部署产品密钥以及管理成功推出的产品更新。 本管理员指南通过各种情境，提供有关在网络环境中进行企业部署的指导。

## <a name="deploy-visual-studio-in-an-enterprise-environment"></a>在企业环境中部署 Visual Studio

::: moniker range="vs-2017"

只要每台目标计算机满足[最低安装要求](/visualstudio/productinfo/vs2017-system-requirements-vs/)，就可以将 Visual Studio 部署到客户端工作站。 无论是通过 System Center 等软件还是通过批处理文件进行部署，通常都需要完成以下步骤：

::: moniker-end

::: moniker range="vs-2019"

只要每台目标计算机满足[最低安装要求](/visualstudio/releases/2019/system-requirements/)，就可以将 Visual Studio 部署到客户端工作站。 无论是通过 System Center 等软件还是通过批处理文件进行部署，通常都需要完成以下步骤：

::: moniker-end

1. 在网络位置上[创建包含 Visual Studio 产品文件的网络共享](create-a-network-installation-of-visual-studio.md)。

2. [选择要安装的工作负载和组件](workload-and-component-ids.md)。

3. [创建包含默认安装选项的响应文件](automated-installation-with-response-file.md)。 或者，[生成安装脚本](use-command-line-parameters-to-install-visual-studio.md)，使用命令行参数来控制安装。

4. （可选）[应用批量许可证产品密钥](automatically-apply-product-keys-when-deploying-visual-studio.md)作为安装脚本的一部分，这样用户便无需单独激活软件。

5. 将网络布局更新为[控制何时向最终用户提供产品更新](controlling-updates-to-visual-studio-deployments.md)。

6. （可选）将注册表项设置为[控制在客户端工作站上缓存什么内容](set-defaults-for-enterprise-deployments.md)。

7. 使用选定的部署技术，在目标开发者工作站上执行前述步骤中生成的脚本。

8. 定期运行第 1 步中的命令来添加更新后的组件，使用 Visual Studio [最新更新刷新网络位置](update-a-network-installation-of-visual-studio.md)。

> [!IMPORTANT]
> 请注意，从网络共享进行安装会“记住”它们的源位置。 这意味着客户端计算机的修复可能需要返回最初从中安装客户端的网络共享。 请谨慎选择网络位置，使其符合在组织中运行的 Visual Studio 客户端的预期生存期。

## <a name="use-visual-studio-tools"></a>使用 Visual Studio 工具

我们提供了几种工具来帮助你在客户端计算机上[检测和管理安装的 Visual Studio 实例](tools-for-managing-visual-studio-instances.md)。

> [!TIP]
> 除了管理员指南中的文档外，[Visual Studio 安装程序存档](https://devblogs.microsoft.com/setup/tag/vs2017/)也是不错的 Visual Studio 安装程序参考信息源。

## <a name="specify-customer-feedback-settings"></a>指定客户反馈设置

默认情况下，Visual Studio 安装会启用客户反馈。 启用“组策略”时，可以将 Visual Studio 配置为在个人计算机上禁用客户反馈。 为此，请在以下键上设置基于注册表的策略：

HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM

Entry = OptIn

Value = (DWORD)
* 0 为选择禁用
* 1 为选择启用

有关客户反馈设置的详细信息，请参阅 [Visual Studio 客户体验改善计划](../ide/visual-studio-experience-improvement-program.md)页。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>请参阅

* [安装 Visual Studio](install-visual-studio.md)
* [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [命令行参数示例](command-line-parameter-examples.md)
  * [工作负载和组件 ID 参考](workload-and-component-ids.md)
* [创建基于网络的 Visual Studio 安装](create-a-network-installation-of-visual-studio.md)
  * [安装 Visual Studio 脱机安装所需的证书](install-certificates-for-visual-studio-offline.md)
* [通过响应文件自动执行 Visual Studio](automated-installation-with-response-file.md)
* [在部署 Visual Studio 时自动应用产品密钥](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [为 Visual Studio 企业部署设置默认值](set-defaults-for-enterprise-deployments.md)
* [禁用或移动包缓存](disable-or-move-the-package-cache.md)
* [更新基于网络的 Visual Studio 安装](update-a-network-installation-of-visual-studio.md)
* [控制 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)
* [用于检测和管理 Visual Studio 实例的工具](tools-for-managing-visual-studio-instances.md)
* [Visual Studio 产品生命周期和维护](/visualstudio/releases/2019/servicing/)
