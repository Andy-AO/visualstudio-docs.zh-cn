---
title: 处理透支的许可证 | Microsoft 文档
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 02/13/2018
ms.topic: conceptual
description: 了解管理员如何解决透支的订阅
searchscope: VS Subscription
ms.openlocfilehash: 06da8c460e9660857b0f03062bde5bd983bd176d
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2019
ms.locfileid: "67587005"
---
# <a name="overallocated-subscriptions"></a>过度分配的订阅

有时，添加订阅者后，订单发生变化，这可能会导致已分配的订阅数量超过公司拥有的许可证数量。 出现这种情况时，“订阅者”选项卡会显示警报并提供详细信息。

> [!NOTE]
> 开放式许可证计划不允许出现透支的情况。  另外，其他程序可能会在门户中以不同方式显示此信息。
>
> [!div class="mx-imgBorder"]
> ![透支订阅通知](_img/over-claimed/over-claimed-alert.png)

## <a name="resolving-overallocated-subscriptions"></a>解决订阅过度分配的问题

要解决许可证过度分配的问题：

1. 单击警报文本。 随即会显示分配到该订阅级别的订阅者筛选列表以及透支到期日期。 

2. 根据需要删除订阅者，以调整透支的许可证。 

3. 页面左侧的概述将更新，以显示你再一次符合规定，并且所有透支通知都将消失。 

## <a name="billing-and-true-up"></a>计费和校正

如果你的组织具有企业协议 (EA)，则管理员无需购买订阅即可分配它们，稍后再通过被称作“校正”的对帐过程支付相关费用。  如果过度分配，则在“校正”期间，将按分配给用户的最大订阅数向你的组织计费。  即使在校正发生期间你分配的订阅数不再达到上限，也是如此。  要详细了解如何监视你的最大用量，请访问[最大用量](maximum-usage.md)主题。

> [!Important]
> 如果 Visual Studio 订阅管理员分配了带有 GitHub Enterprise 的 Visual Studio 订阅，且从未购买过这些订阅，则它们将对组织中的 GitHub Enterprise 管理员不可见。 要确保 GitHub Enterprise 订阅可见，应在首次分配订阅时至少购买一个带 GitHub Enterprise 的 Visual Studio Professional 订阅或带 GitHub Enterprise 的 Visual Studio Enterprise 订阅  。  
>
> 由客户负责确保在管理门户中针对所分配的每个 GitHub 订阅都分配了一个对应的带 GitHub 的 Visual Studio 订阅，从而保证符合此订阅的许可要求。

详细了解如何管理[带有 GitHub Enterprise 的 Visual Studio 订阅](assign-github.md)。

## <a name="support-resources"></a>支持资源

- 有关 Visual Studio 订阅的销售、订阅、帐户和账单的帮助，请与 Visual Studio [订阅支持](https://visualstudio.microsoft.com/subscriptions/support/)联系。
