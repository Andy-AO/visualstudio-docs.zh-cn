---
title: Visual Studio 订阅者数据匿名化 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 10/31/2018
ms.topic: conceptual
description: 了解订阅访问丢失时订阅者数据的匿名方式。
ms.openlocfilehash: 1d4e4c5f2e1946a75a70ab4ddb49f000c951cd97
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783657"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Visual Studio 订阅者信息匿名化

当发生阻止订阅者使用订阅的事件时，例如订阅到期或删除订阅者的登录帐户，用户的个人信息（如姓名和登录帐户）基本上被扰乱以使其无法使用。  这样做是为了保护订阅者的个人信息。

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>何时发生匿名？

致使订阅者无法订阅的事件将触发匿名。  匿名发生的速度取决于订阅类型和触发事件。 有关详细信息，请参阅下表。

| 订阅类型                                                                                                                       | 触发匿名的事件                                                                                                     | 匿名发生时 |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | 订阅者选择退出该计划或不接受使用条款                                    | 30 天               |
| 通过 Microsoft Store（零售）购买的 Visual Studio 订阅                                                                      | 订阅过期或没有激活                                                                   | 360 天                  |
| 通过 Volume License、Visual Studio Marketplace（云订阅）或 MPN 等计划获得的 Visual Studio 订阅 | 订阅过期或未分配给用户                                                          | 180 天                  |
| 所有订阅                                                                                                                       | 用于登录订阅的 Azure Active Directory 帐户或 Microsoft 帐户 (MSA) 已关闭 | 立即               |
| 所有订阅                                                                                                                       | 将从与 Azure Active Directory 帐户关联的租户中删除订阅者                                | 立即               |

## <a name="faq"></a>FAQ

### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>问：订阅者个人信息匿名化是否导致他们无法访问订阅？
答：不是。  匿名化是针对导致订阅权限丢失但不导致缺乏访问权限的事件而进行的。

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>问：我是组织的订阅的管理员。  如果某个订阅者的信息是匿名的，那么该订阅是否可以重新分配给其他用户？
答：是的 - 只要订阅尚未过期，就可以将其重新分配给其他订阅者。

## <a name="next-steps"></a>后续步骤

通过[链接 MSA 和 AAD 标识](/azure/active-directory/b2b/add-users-administrator)了解如何防止匿名。
