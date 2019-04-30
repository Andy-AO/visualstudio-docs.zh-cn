---
title: 部署 ClickOnce 应用程序进行测试和生产服务器无需重新签名 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d573de9889d286a7b634890e0d8b469541bc741f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407055"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>无需重新签名部署 ClickOnce 应用程序测试和生产服务器
本文介绍 ClickOnce 在.NET Framework 版本 3.5，而无需重新签名或更改 ClickOnce 使从多个网络位置的 ClickOnce 应用程序的部署清单中引入的一项功能。

> [!NOTE]
> 重新签名仍是用于部署新版本的应用程序的首选的方法。 只要有可能，使用重新签名的方法。 有关详细信息，请参阅 [Mage.exe（清单生成和编辑工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)。

 第三方开发人员和 Isv 可以选择启用此功能，使其客户更新他们的应用程序更轻松。 在以下情况下，可以使用此功能：

- 当更新不用于应用程序首次安装的应用程序。

- 当一台计算机上的应用程序只有一个配置。 例如，如果应用程序配置为指向两个不同的数据库，不能使用此功能。

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>从部署清单中排除 deploymentProvider
 在.NET Framework 2.0 和.NET Framework 3.0 中，在脱机可用性的系统安装任何 ClickOnce 应用程序必须列出`deploymentProvider`在其部署清单中。 `deploymentProvider`通常称为更新位置中; 它是在其中 ClickOnce 检查应用程序更新的位置。 此要求，以及为应用程序发布者登录他们的部署，需要进行很难更新 ClickOnce 应用程序供应商或其他第三方公司。 它还使更难以部署在同一网络上的多个位置提供的相同应用程序。

 对.NET Framework 3.5 中的 ClickOnce 所做的更改，就可以为第三方提供到另一个组织，然后可以将其自身的网络上的应用程序部署的 ClickOnce 应用程序。

 若要充分利用此功能，ClickOnce 应用程序的开发人员必须排除`deploymentProvider`从其部署清单。 这一要求意味着，必须排除`-providerUrl`使用 Mage.exe 清单创建部署时的参数。 或者，如果要生成使用 MageUI.exe 部署清单进行签名，必须确保**启动位置**上的文本框中**应用程序清单**选项卡上保留为空。

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider 和应用程序更新
 从.NET Framework 3.5 开始，不再需要指定`deploymentProvider`为了部署联机和脱机使用情况的 ClickOnce 应用程序部署清单中。 此更改支持方案中，您需要用来打包和签名部署你自己，但是对其他公司通过其网络部署应用程序。

 需要记住的重要一点是，应用程序排除`deploymentProvider`不能更改其安装位置期间更新，直到它们寄送包含的更新`deploymentProvider`再次标记。

 下面是两个示例来说明这一点。 在第一个示例中，发布 ClickOnce 应用程序不具有`deploymentProvider`标记，，并要求用户从 http://www.adatum.com/MyApplication/ 。 如果你决定想要发布的应用程序的下一个更新 http://subdomain.adatum.com/MyApplication/，没有任何办法来表明此驻留在的部署清单中的 http://www.adatum.com/MyApplication/ 。 您可以执行两个操作之一：

- 告知用户卸载以前的版本，并从新位置中安装新版本。

- 包括在更新 http://www.adatum.com/MyApplication/，其中包含 `deploymentProvider` 指向 http://www.adatum.com/MyApplication/ 。 然后，释放更高版本与另一个更新 `deploymentProvider` 指向 http://subdomain.adatum.com/MyApplication/ 。

  在第二个示例中，发布 ClickOnce 应用程序指定`deploymentProvider`，然后决定将其删除。 一次新版本而无需`deploymentProvider`下载客户端，您不能将重定向到之前发布了应用程序的版本，用于更新的路径`deploymentProvider`还原。 与第一个示例一样`deploymentProvider`最初必须指向当前的更新位置，而不是新位置。 在此情况下，如果你尝试插入`deploymentProvider`，是指 http://subdomain.adatum.com/MyApplication/，则下一次更新将失败。

## <a name="create-a-deployment"></a>创建部署
 有关创建可从不同的网络位置部署的部署的分步指导，请参阅[演练：手动部署 ClickOnce 应用程序，不需要重新签名并且保留署名信息](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)。

## <a name="see-also"></a>请参阅
- [*Mage.exe*（清单生成和编辑工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe*（图形化客户端中的清单生成和编辑工具）](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)