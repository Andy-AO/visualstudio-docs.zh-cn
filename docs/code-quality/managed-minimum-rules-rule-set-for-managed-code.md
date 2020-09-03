---
title: 托管代码的“托管最少量规则”规则集
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 95264aafd2467065ee2bc36d463369f19714dd68
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "75587350"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>托管代码的“托管最少量规则”规则集

托管的最小规则侧重于代码中最关键的问题，包括潜在的安全漏洞、应用程序崩溃和其他重要的逻辑和设计错误。 在为项目创建的任何自定义规则集中包含此规则集。

|规则|描述|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|具有可释放字段的类型应该是可释放的|
|[CA1821](../code-quality/ca1821.md)|移除空终结器|
|[CA2213](../code-quality/ca2213.md)|应释放可释放的字段|
|[CA2231](../code-quality/ca2231.md)|重写时重载相等运算符 `ValueType.Equals`|
