---
title: Otherwise 元素 (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Otherwise
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: acf285c895e5160e850b6bc8f20f920279a5e26c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59659275"
---
# <a name="otherwise-element-msbuild"></a>Otherwise 元素 (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定当且仅当所有 `When` 元素的条件的计算结果为 `false` 时才执行的代码块。  
  
 \<Project>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  
  
## <a name="syntax"></a>语法  
  
```  
<Otherwise>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</Otherwise>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
  
|元素|说明|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|可选元素。<br /><br /> 评估子元素以选择代码的一部分来执行。 `Choose` 元素中可能有零个或零个以上的 `Otherwise` 元素。|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|可选元素。<br /><br /> 包含一组用户定义的 [Item](../msbuild/item-element-msbuild.md) 元素。 `ItemGroup` 元素中可能有零个或零个以上的 `Otherwise` 元素。|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|可选元素。<br /><br /> 包含一组用户定义的 [Property](../msbuild/property-element-msbuild.md) 元素。 `PropertyGroup` 元素中可能有零个或零个以上的 `Otherwise` 元素。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|评估子元素以选择代码的一部分来执行。|  
  
## <a name="remarks"></a>备注  
 `Choose` 元素中可能只有一个 `Otherwise`元素，并且它必须是最后一个元素。  
  
 `Choose`、`When` 和 `Otherwise` 元素一起用来提供一种方式，通过这种方式选择代码的一部分来执行许多种可能的替代选择。 有关详细信息，请参阅[条件构造](../msbuild/msbuild-conditional-constructs.md)。  
  
## <a name="example"></a>示例  
 以下项目使用 `Choose` 元素来选择要在 `When` 元素中设置的属性值组。 如果两个 `When` 元素的 `Condition` 属性的计算结果均为 `false`，则将设置 `Otherwise` 元素中的属性值。  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='debug' ">  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <DebugType>full</DebugType>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\Debug\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
            <ItemGroup>  
                <Compile Include="UnitTesting\*.cs" />  
                <Reference Include="NUnit.dll" />  
            </ItemGroup>  
        </When>  
        <When Condition=" '$(Configuration)'=='retail' ">  
            <PropertyGroup>  
                <DebugSymbols>false</DebugSymbols>  
                <Optimize>true</Optimize>  
                <OutputPath>.\bin\Release\</OutputPath>  
                <DefineConstants>TRACE</DefineConstants>  
            </PropertyGroup>  
        </When>  
        <Otherwise>  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\$(Configuration)\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
        </Otherwise>  
        </Choose>  
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
</Project>  
```  
  
## <a name="see-also"></a>请参阅  
 [条件构造](../msbuild/msbuild-conditional-constructs.md)   
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)
