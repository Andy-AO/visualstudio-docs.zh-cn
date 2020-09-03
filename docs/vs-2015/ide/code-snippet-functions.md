---
title: 代码段函数 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 92533b90e6a2da9f29a67d13c6e0eee2c31dbcfe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72620236"
---
# <a name="code-snippet-functions"></a>代码段函数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

有三个函数可与 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 代码片段一起使用。 函数在代码片段的 [Function](https://msdn.microsoft.com/572c5549-5821-4e15-8ecd-0fa86c1c65df) 元素中指定。 有关创建代码片段的详细信息，请参阅[代码片段](../ide/code-snippets.md)。

## <a name="functions"></a>函数
 下表介绍可与代码片段中的 `Function` 元素一起使用的函数。

|函数|说明|语言|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|为 `EnumerationLiteral` 参数指定的枚举成员生成一个switch 语句和一组 case 语句。 `EnumerationLiteral` 参数必须是枚举文本的引用或是枚举类型。|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|
|`ClassName()`|返回包含插入的代码片段的类的名称。|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|
|`SimpleTypeName(` `TypeName` `)`|在已调用该代码片段的上下文中将 TypeName 参数缩减为其最简单的形式  。|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|

## <a name="example"></a>示例
 以下示例演示如何使用 `GenerateSwitchCases` 函数。 在插入此代码片段并将枚举输入到 `$switch_on$` 文本中时，`$cases$` 文本为枚举中的每个值生成一个 `case` 语句。

```
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>switch</Title>
            <Shortcut>switch</Shortcut>
            <Description>Code snippet for switch statement</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>expression</ID>
                    <ToolTip>Expression to switch on</ToolTip>
                    <Default>switch_on</Default>
                </Literal>
                <Literal Editable="false">
                    <ID>cases</ID>
                    <Function>GenerateSwitchCases($expression$)</Function>
                    <Default>default:</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    switch ($expression$)
                    {
                        $cases$
                    }
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="example"></a>示例
 以下示例演示如何使用 `ClassName` 函数。 在插入此代码片段时，`$classname$` 文本会替换为代码文件中该位置的封闭类的名称。

```
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Common constructor pattern</Title>
            <Shortcut>ctor</Shortcut>
            <Description>Code Snippet for a constructor</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>type</ID>
                    <Default>int</Default>
                </Literal>
                <Literal>
                    <ID>name</ID>
                    <Default>field</Default>
                </Literal>
                <Literal default="true" Editable="false">
                    <ID>classname</ID>
                    <ToolTip>Class name</ToolTip>
                    <Function>ClassName()</Function>
                    <Default>ClassNamePlaceholder</Default>
                </Literal>
            </Declarations>
            <Code Language="vjsharp" Format="CData">
                <![CDATA[
                    public $classname$ ($type$ $name$)
                    {
                        this._$name$ = $name$;
                    }
                    private $type$ _$name$;
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="example"></a>示例
 此示例演示如何使用 `SimpleTypeName` 函数。 在此代码片段插入到代码文件中时，`$SystemConsole$` 文本会替换为在其中调用该代码片段的上下文中 <xref:System.Console> 类型的最简单形式。

```
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Console_WriteLine</Title>
            <Shortcut>cw</Shortcut>
            <Description>Code snippet for Console.WriteLine</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal Editable="false">
                    <ID>SystemConsole</ID>
                    <Function>SimpleTypeName(global::System.Console)</Function>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    $SystemConsole$.WriteLine();
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>另请参阅
 [函数元素 (Intellisense 代码片段) ](https://msdn.microsoft.com/572c5549-5821-4e15-8ecd-0fa86c1c65df) [代码段架构参考](../ide/code-snippets-schema-reference.md)
