---
title: 如何：在生成中使用环境变量 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 78cdc8f95c5a48e8ce0491926b27f0521705e3bb
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59655876"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>如何：在生成中使用环境变量
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在生成项目时，有时经常需要使用非项目文件或构成项目的文件中的信息来设置生成选项。 此信息通常存储在环境变量中。  
  
## <a name="referencing-environment-variables"></a>引用环境变量  
 所有环境变量均可供 [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) 项目文件作为属性使用。  
  
> [!NOTE]
>  如果项目文件包含与环境变量具有相同名称的属性的显式定义，则项目文件中的属性将替代环境变量的值。  
  
#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>在 MSBuild 项目中使用环境变量  
  
- 以引用项目文件中声明的变量相同的方式引用环境变量。 例如，以下代码引用 BIN_PATH 环境变量：  
  
   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`  
  
  如果未设置环境变量，则可以使用 `Condition` 属性来提供属性的默认值。  
  
#### <a name="to-provide-a-default-value-for-a-property"></a>提供属性的默认值  
  
-   仅当某属性不具有任何值时，使用该属性上的 `Condition` 特性来设置值。 例如，仅在未设置 `ToolsPath` 环境变量时，以下代码才将 `ToolsPath` 属性设置为 c:\tools：  
  
     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`  
  
    > [!NOTE]
    >  属性名称不区分大小写，因此 `$(ToolsPath)` 和 `$(TOOLSPATH)` 均引用相同的属性或环境变量。  
  
## <a name="example"></a>示例  
 以下项目文件使用环境变量来指定目录的位置。  
  
```  
<Project DefaultTargets="FakeBuild">  
    <PropertyGroup>  
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>  
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">  
            C:\Tools  
        </ToolsPath>  
    </PropertyGroup>  
    <Target Name="FakeBuild">  
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>请参阅  

[MSBuild](msbuild.md)

[MSBuild 属性](../msbuild/msbuild-properties1.md)

[如何：生成相同的源文件使用不同选项](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
