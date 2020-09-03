---
title: DSL 定义的属性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8755b1b70051c54157fa87ee0b66dbc9340b5024
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668471"
---
# <a name="properties-of-a-dsl-definition"></a>DSL 定义的属性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dsldefinition.dsl 属性定义 *域特定语言* 定义属性，如版本编号。 单击*特定于域的语言设计器*中的关系图区域时，dsldefinition.dsl 属性将显示在 "**属性**" 窗口中。

 有关详细信息，请参阅 [如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)。 有关如何使用这些属性的详细信息，请参阅 [自定义和扩展域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

 Dsldefinition.dsl 具有下表中的属性：

|属性|说明|默认|
|--------------|-----------------|-------------|
|访问修饰符|确定域类的访问修饰符是公共的还是内部的。|公共|
|自定义特性|域类的自定义属性。<br /><br /> **注意** 使用 "浏览" 按钮添加属性。|\<none>|
|公司名称|系统注册表中当前公司名称的名称。|当前公司名称|
|名称|此域类的名称。|当前名称|
|命名空间|与此域类关联的命名空间。|当前命名空间|
|包 Guid|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]为此 DSL 生成的包的 guid。|\<none>|
|包命名空间|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]为此 DSL 生成的包的命名空间。|\<none>|
|产品名称|将为 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 为此 DSL 生成的包注册的产品名称。|\<none>|
|备注|与此域类关联的注释。|\<none>|
|说明|此域类的说明。|\<none>|
|显示名称|将在此域类的生成的设计器中显示的名称。|\<none>|
|帮助关键字|与此域类关联的帮助关键字。|\<none>|
|生成|此域特定语言定义的递增生成号。|0|
|主要版本|此域特定语言定义的递增主要版本号。|1|
|次要版本|此域特定语言定义的递增次内部版本号。|0|
|修订|此域特定语言定义的递增修订版本号。|0|

## <a name="see-also"></a>另请参阅
 [域特定语言工具术语表](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
