---
title: 演练：创建代码片段
ms.date: 10/27/2017
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: d717619954981c6b8cdf900f8fb358272478264b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62581667"
---
# <a name="walkthrough-create-a-code-snippet"></a>演练：创建代码片段

只需几步操作即可创建代码片段。 你需要做的就是创建一个 XML 文件，填写适当的元素，并向其中添加代码。 此外还可以向代码中添加引用和替换参数。 可以在“代码片段管理器”（“工具” > “代码片段管理器”）中使用“导入”按钮向 Visual Studio 的安装添加代码片段。

## <a name="snippet-template"></a>代码片段模板

以下是基本代码片段模板：

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title></Title>
        </Header>
        <Snippet>
            <Code Language="">
                <![CDATA[]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

### <a name="create-a-code-snippet"></a>创建代码片段

1. 在 Visual Studio 中创建新的 XML 文件，然后添加如上所示的模板。

2. 在元素中填写代码片段的标题，例如在 Title 元素中填写“Hello World VB”。

3. 在 Code 元素的“语言”属性中填写代码片段的语言。 对于本示例，请使用“VB”。

4. 在 Code 元素中的 CDATA 部分内添加某些代码，例如：

    ```xml
    <Code Language="VB">
        <![CDATA[Console.WriteLine("Hello, World!")]]>
    </Code>
    ```

5. 将代码片段另存为 VBCodeSnippet.snippet。

### <a name="add-a-code-snippet-to-visual-studio"></a>将代码片段添加到 Visual Studio

1. 可以使用代码片段管理器将自己的代码片段添加到 Visual Studio 安装。 打开“代码片段管理器”（“工具” > “代码片段管理器”）。

2. 单击“导入”按钮。

3. 请转到在前面的过程中保存代码片段的位置，选择该位置，然后单击“打开”。

4. “导入代码片段”对话框随即打开，要求从右窗格中提供的选项中选择代码片段的添加位置。 其中一个选项应为“我的代码片段”。 选择它，单击“完成”，然后单击“确定”。

5. 代码片段会复制到以下位置：

   ::: moniker range="vs-2017"

   %USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippets

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

6. 通过打开 Visual Basic 项目并打开代码文件，测试代码片段。 在文件中，依次选择右键单击菜单中的“代码片段” > “插入代码片段”，再选择“我的代码片段”。 应看到一个名为“我的 Visual Basic 代码片段”的代码片段。 双击该选项。

    `Console.WriteLine("Hello, World!")` 会插入到代码文件中。

### <a name="add-description-and-shortcut-fields"></a>添加“说明”和“快捷方式”字段

::: moniker range="vs-2017"

1. 在“代码片段管理器”中查看“说明”字段时，可以获得有关代码片段的详细信息。 快捷方式是用户为插入代码片段而键入的标记。 通过打开文件 %USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet，编辑已添加的代码片段。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在“代码片段管理器”中查看“说明”字段时，可以获得有关代码片段的详细信息。 快捷方式是用户为插入代码片段而键入的标记。 通过打开文件 *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet*，编辑已添加的代码片段。

::: moniker-end

2. 将 Author 和 Description 元素添加到 Header 元素，并填写。

3. Header 元素应该类似于以下形式：

    ```xml
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
    </Header>
    ```

4. 打开“代码片段管理器”并选择代码片段。 在右窗格中，应看到“说明”和“创建者”字段已填写。

5. 要添加快捷方式，请添加 Shortcut 元素，以及 Author 和 Description 元素：

    ```xml
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
        <Shortcut>hello</Shortcut>
    </Header>
    ```

6. 再次保存代码片段文件。

7. 要测试该快捷方式，请打开 Visual Basic 项目，并打开代码文件。 在文件中键入 `hello`，然后按两次 Tab。

    代码片段代码已插入。

### <a name="add-references-and-imports"></a>添加引用和导入

1. 借助 References 元素可以添加对项目的引用，借助 Imports 元素可以添加导入声明。 （这也适用于 C#。）例如，如果将代码示例中的 `Console.WriteLine` 更改为 `MessageBox.Show`，则可能需要将 System.Windows.Forms.dll 程序集添加到项目中。

2. 打开代码片段。

3. 在 Snippet 元素下添加 References 元素：

    ```xml
    <References>
        <Reference>
            <Assembly>System.Windows.Forms.dll</Assembly>
        </Reference>
    </References>
    ```

4. 在 Snippet 元素下添加 Imports 元素：

    ```xml
    <Imports>
        <Import>
           <Namespace>System.Windows.Forms</Namespace>
        </Import>
    </Imports>
    ```

5. 将 CDATA 部分更改为以下内容：

    ```xml
    <![CDATA[MessageBox.Show("Hello, World!")]]>
    ```

6. 保存代码片段。

7. 打开 Visual Basic 项目并添加代码片段。

8. 代码文件顶部会出现一条 `Imports` 语句：

    ```vb
    Imports System.Windows.Forms
    ```

9. 查看项目的属性。 “引用”选项卡包括对 System.Windows.Forms.dll 的引用。

### <a name="add-replacements"></a>添加替换

1. 你可能需要用户替换部分代码片段，例如，如果添加了一个变量并需要用户将该变量替换为当前项目中的变量。 可以提供两种类型的替换：文本和对象。 文本是某些类型的字符串（字符串文本、变量名称或数值的字符串表示形式）。 对象是除字符串以外的其他类型的实例。 在此过程中，需要声明文本替换和对象替换，并更改代码，以引用这些替换。

2. 打开代码片段。

3. 此示例使用 SQL 连接字符串，因此需要更改 Imports 和 References 元素，以添加合适的引用：

    ```xml
    <References>
        <Reference>
            <Assembly>System.Data.dll</Assembly>
        </Reference>
        <Reference>
            <Assembly>System.Xml.dll</Assembly>
        </Reference>
    </References>
    <Imports>
        <Import>
            <Namespace>System.Data</Namespace>
        </Import>
        <Import>
            <Namespace>System.Data.SqlClient</Namespace>
        </Import>
    </Imports>
    ```

4. 要声明 SQL 连接字符串的文本替换，请在 Snippet 元素下添加 Declarations 元素，并在其中添加具有 ID、工具提示和替换默认值子元素的 Literal 元素：

    ```xml
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
    </Declarations>
    ```

5. 要声明 SQL 连接的对象替换，请在 Declarations 元素内添加 Object 元素，并添加 ID、对象类型、工具提示和默认值子元素。 生成的 Declarations 元素应如下所示：

    ```xml
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
        <Object>
            <ID>SqlConnection</ID>
            <Type>System.Data.SqlClient.SqlConnection</Type>
            <ToolTip>Replace with a connection object in your application.</ToolTip>
            <Default>dcConnection</Default>
        </Object>
    </Declarations>
    ```

6. 在代码部分中，可以用 $ 符号包围替换内容进行引用，例如 `$replacement$`：

    ```xml
    <Code Language="VB" Kind="method body">
        <![CDATA[Dim daCustomers As SqlDataAdapter
            Dim selectCommand As SqlCommand

            daCustomers = New SqlClient.SqlDataAdapter()
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)
            daCustomers.SelectCommand = selectCommand
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>
    </Code>
    ```

7. 保存代码片段。

8. 打开 Visual Basic 项目并添加代码片段。

9. 代码应如下所示，其中 `SQL connection string` 和 `dcConnection` 替换内容以浅橙色突出显示。 选择 Tab 可在替换内容之间导航。

    ```vb
    Dim daCustomers As SqlDataAdapter
    Dim selectCommand As SqlCommand

    daCustomers = New SqlClient.SqlDataAdapter()
    selectCommand = New SqlClient.SqlCommand("SQL connection string")
    daCustomers.SelectCommand = selectCommand
    daCustomers.SelectCommand.Connection = dcConnection
    ```

## <a name="see-also"></a>请参阅

- [代码片段架构参考](../ide/code-snippets-schema-reference.md)