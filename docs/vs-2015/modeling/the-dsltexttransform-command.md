---
title: DslTextTransform 命令 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 599bf14a3d37fbd6bdff111f79e658f44624792b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658466"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform 命令
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform 是一个脚本，它调用 TextTransform.exe 并使用常用选项运行它。 可以使用 DslTextTransformation 自动执行项目的夜间生成 [!INCLUDE[dsl](../includes/dsl-md.md)] 。 有关详细信息，请参阅 [用 TextTransform 实用工具生成文件](../modeling/generating-files-with-the-texttransform-utility.md)。

 DslTextTransform 位于以下目录中：

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 可以将以下参数指定为 DslTextTransform 的输入：

- 域模型项目的输出目录。

- 设计器定义项目的输出目录。

- 文本模板文件的位置。

  DslTextTransform 使用默认指令处理器和程序集处理指定的文本模板文件。 如果创建自定义指令处理器，则可以创建自己的批处理文件来调用 TextTransform.exe。 在此批处理文件中，可以指定程序集和关联的自定义指令处理器。
