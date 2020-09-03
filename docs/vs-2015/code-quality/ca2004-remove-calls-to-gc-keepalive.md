---
title: CA2004：删除对 GC 的调用。KeepAlive |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53fa5f61cb7c503502956831452bc3eca1a9fece
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521194"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004:移除对 GC.KeepAlive 的调用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|项|值|
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|类别|Microsoft 可靠性|
|是否重大更改|不间断|

## <a name="cause"></a>原因
 类使用 `SafeHandle` 但仍包含对的调用 `GC.KeepAlive` 。

## <a name="rule-description"></a>规则描述
 如果要转换为 `SafeHandle` 用法，请删除对 `GC.KeepAlive` (对象) 的所有调用。 在这种情况下，类不应调用 `GC.KeepAlive` ，前提是它们没有终结器，而是依赖 `SafeHandle` 于完成它们的操作系统句柄。  尽管对的调用的开销 `GC.KeepAlive` 可能会因为性能的衡量而忽略不计，但从角度来看，对的调用 `GC.KeepAlive` 是必要的或足以解决可能不再存在的生存期问题，这会使代码更难以维护。

## <a name="how-to-fix-violations"></a>如何解决冲突
 删除对 `GC.KeepAlive` 的调用。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 仅当在技术上不能转换为 `SafeHandle` 类中的使用情况时，才可以禁止显示此警告。
