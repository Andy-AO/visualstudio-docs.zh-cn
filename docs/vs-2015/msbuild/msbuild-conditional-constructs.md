---
title: MSBuild 条件构造 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b7b22f63d5d3d6e0b1f7789561029bbfbfb4cdf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143772"
---
# <a name="msbuild-conditional-constructs"></a>MSBuild 的条件构造
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 提供一种机制，用于通过 [选择](../msbuild/choose-element-msbuild.md)、 [When](../msbuild/when-element-msbuild.md)和 [其他](../msbuild/otherwise-element-msbuild.md) 元素进行处理。  
  
## <a name="using-the-choose-element"></a>使用 Choose 元素  
 `Choose` 元素包含一系列具有 `Condition` 属性的 `When` 元素，这些元素按照从顶部到底部的顺序进行测试，直到一个元素的计算结果为 `true`。 如果多个 `When` 元素的计算结果为 `true`，则只使用第一个。 如果 `When` 元素的任何条件的计算结果均为 `true`，则评估 `Otherwise` 元素（如存在）。  
  
 `Choose` 元素可用作 `Project`、`When` 和 `Otherwise` 元素的子元素。 `When` 和 `Otherwise` 元素可具有 `ItemGroup`、`PropertyGroup` 或 `Choose` 子元素。  
  
## <a name="example"></a>示例  
 以下示例使用 `Choose` 和 `When` 元素进行非此即彼的处理。 根据 `Configuration` 属性的值设置项目的属性和项。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='Debug' ">  
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
    </Choose>  
    <!-- Rest of Project -->  
</Project>  
```  
  
## <a name="see-also"></a>另请参阅  
 [选择元素 (MSBuild) ](../msbuild/choose-element-msbuild.md)   
 [当元素 (MSBuild) ](../msbuild/when-element-msbuild.md)   
 [否则为 (MSBuild) 的元素 ](../msbuild/otherwise-element-msbuild.md)   
 [MSBuild 引用](../msbuild/msbuild-reference.md)
