---
title: 如何：指定首先生成的目标 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7e1c9c4374e35dd484d478118fe714ff415f93e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654875"
---
# <a name="how-to-specify-which-target-to-build-first"></a>如何：指定首先生成的目标
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

项目文件可以包含一个或多个用于定义如何生成项目的 `Target` 元素。 [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) 引擎生成它找到的第一个项目，以及任何依赖项，除非项目文件包含 `DefaultTargets` 属性、`InitialTargets` 属性或者目标是在命令行中使用 **/target** 开关指定的。  
  
## <a name="using-the-initialtargets-attribute"></a>使用 InitialTargets 属性  
 `Project` 元素的 `InitialTargets` 属性指定将首先运行的目标，即使在命令行或 `DefaultTargets` 属性中指定了目标。  
  
#### <a name="to-specify-one-initial-target"></a>指定一个初始目标  
  
- 在 `Project` 元素的 `InitialTargets` 属性中指定默认目标。 例如：  
  
   `<Project InitialTargets="Clean">`  
  
  可以通过按顺序列出目标并使用分号来分隔每个目标，在 `InitialTargets` 属性中指定多个初始目标。 列表中的目标将按顺序运行。  
  
#### <a name="to-specify-more-than-one-initial-target"></a>指定多个初始目标  
  
-   在 `Project` 元素的 `InitialTargets` 属性中列出初始目标，用分号分隔。 例如，若要运行 `Clean` 目标，然后运行 `Compile` 目标，则键入：  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>使用 DefaultTargets 属性  
 `Project` 元素的 `DefaultTargets` 属性指定如果未在命令行上显式指定目标，将生成哪个或哪些目标。 如果在 `InitialTargets` 和 `DefaultTargets` 属性中均指定了目标，而未在命令行上指定任何目标，则 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 先运行在 `InitialTargets` 属性中指定的目标，然后再运行在 `DefaultTargets` 属性中指定的目标。  
  
#### <a name="to-specify-one-default-target"></a>指定一个默认目标  
  
- 在 `Project` 元素的 `DefaultTargets` 属性中指定默认目标。 例如：  
  
   `<Project DefaultTargets="Compile">`  
  
  可以通过按顺序列出目标并使用分号来分隔每个目标，在 `DefaultTargets` 属性中指定多个默认目标。 列表中的目标将按顺序运行。  
  
#### <a name="to-specify-more-than-one-default-target"></a>指定多个默认目标  
  
-   在 `Project` 元素的 `DefaultTargets` 属性中列出默认目标，用分号分隔。 例如，若要运行 `Clean` 目标，然后运行 `Compile` 目标，则键入：  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>使用 /target 开关  
 如果未在项目文件中定义默认目标，或者如果你不想使用该默认目标，则可以使用命令行开关 **/target** 来指定不同的目标。 使用 **/target** 开关指定的一个或多个目标将代替 `DefaultTargets` 属性指定的目标运行。 `InitialTargets` 属性中指定的目标将始终首先运行。  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>首先使用非默认目标的目标  
  
-   使用 **/target** 命令行开关将目标指定为第一个目标。 例如：  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>首先使用非默认目标的多个目标  
  
-   使用 **/target** 命令行开关列出目标，用分号或逗号分隔。 例如：  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>请参阅
  [MSBuild](msbuild.md)  
 [目标](../msbuild/msbuild-targets.md)   
 [如何：清理生成](../msbuild/how-to-clean-a-build.md)
