---
title: 代码分析问题疑难解答 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: erickson-doug
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4816783edabbd93fbb536c94f2638fcb4f8d6bb3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60043050"
---
# <a name="troubleshooting-code-analysis-issues"></a>代码分析问题疑难解答
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题包含以下 Visual Studio 代码分析问题的疑难解答信息。  
  
- [Visual Studio 2010 规则集中的更改未反映在以前的 Visual Studio 版本中](#ChildRuleSetChangesInPreviousVersions)  
  
## <a name="ChildRuleSetChangesInPreviousVersions"></a>Visual Studio 2010 规则集中的更改未反映在以前的 Visual Studio 版本中  
 在包含子规则集的 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 中创建规则集时，对子规则集的更改不会应用到使用 Visual Studio 早期版本的计算机上的代码分析运行中。 若要解决此问题，必须强制执行对父规则集（即包含子规则集的规则集）的重写。  
  
1. 打开 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 中的父规则集。  
  
2. 对规则集进行更改，例如添加或删除规则，然后保存。  
  
3. 重新打开此规则集，撤消更改，然后再次保存。  
  
## <a name="see-also"></a>请参阅  
 [分析应用程序质量](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [分析托管代码质量](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [使用规则集对代码分析规则进行分组](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
