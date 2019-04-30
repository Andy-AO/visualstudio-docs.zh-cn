---
title: 从 UML 类图生成代码 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates.TextTransformationDataCollectionEditor
helpviewer_keywords:
- code generation, UML class diagrams
- class diagrams - UML, generating code
- UML diagrams, generating code
ms.assetid: 2790e64d-7728-4c2e-a4dd-4131e795f730
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c95a361f00e9b744aa78f443ad7c173209a5a0bd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442428"
---
# <a name="generate-code-from-uml-class-diagrams"></a>从 UML 类关系图生成代码
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要从 Visual Studio 中的 UML 类图生成 Visual C#.NET 代码，请使用**生成代码**命令。 默认情况下，此命令为你选择的每个 UML 类型生成一个 C# 类型。 可以通过修改或复制生成代码的文本模板来修改和扩展此行为。 可以为包含在模型中不同的包中的类型指定不同的行为。  

 **生成代码**命令是特别适合从用户的所选内容的元素，生成代码和生成每个 UML 类或其他元素的一个文件。 例如，屏幕快照显示了已从两个 UML 类生成的两个 C# 文件。  

 或者，如果你想要生成的代码生成的文件不具有 1 对 1 关系与 UML 元素，则可以考虑编写文本模板调用的**转换所有模板**命令。 有关此方法的详细信息，请参阅[从 UML 模型生成文件](../modeling/generate-files-from-a-uml-model.md)。  

 ![UML 类关系图和生成的 C&#35;类文件。](../modeling/media/oob-gencode1.png "oob_GenCode1")  

 有关在 Visual Studio 中的 UML 类关系图的详细信息，请参阅以下主题：  

- [UML 类关系图：参考](../modeling/uml-class-diagrams-reference.md)  

- [UML 类关系图：指南](../modeling/uml-class-diagrams-guidelines.md)  

  若要查看支持 UML 类图的 Visual Studio 版本，请参阅[体系结构和建模工具的版本支持](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  

## <a name="using-the-generate-code-command"></a>使用生成代码命令  
 下面的过程描述的默认行为**生成代码**命令：  

#### <a name="to-generate-a-separate-file-for-each-element"></a>为每个元素生成一个单独的文件  

1. 创建一个包含类的 UML 模型。 你可能希望将构造型应用于模型元素。  

    有关详细信息，请参阅[默认代码生成转换](#default)。  

2. 在类图上或在**UML 模型资源管理器**，选择你想要生成的代码元素。 可以选择下列项目之一：  

   - 一组特定元素。  

   - 一个包或模型，以便从其内容生成代码。  

   - 关系图，以便选择关系图上的所有元素。  

3. 打开所选元素的快捷菜单，然后选择**生成代码**。  

    使用第一次**生成代码**在特定模型中，会出现一个对话框。 使用此对话框可以编辑模型的代码生成参数。  

    选择**确定**除非你知道你想要更改这些参数。  

    若要稍后返回此对话框中，打开**UML 模型资源管理器**。 打开建模项目快捷菜单，然后选择**设置代码生成**。 有关详细信息，请参阅[自定义生成代码命令](#custom)。  

   将生成包含 C# 代码的文件。 默认情况下，为每个类型生成一个文件，这些文件是在 C# 类库项目中生成的。 不过，你可以自定义此行为。 有关详细信息，请参阅[自定义生成代码命令](#custom)。  

   将一些验证测试应用于模型以确保能将其转换为 C#。 如果这些测试失败，则将显示一条错误消息，并且不执行代码生成操作。 如果你创建了一个验证菜单命令，则不会为其验证命令失败的任何元素生成代码。 有关详细信息，请参阅[为 UML 模型定义验证约束](../modeling/define-validation-constraints-for-uml-models.md)。  

## <a name="default"></a> 默认代码生成转换  
 本部分汇总了所生成的结果**生成代码**命令，除非你自定义命令。 有关详细信息，请参阅[自定义生成代码命令](#custom)。  

- 为你在 UML 模型中选择的每个类型生成一个 C# 类型。 每个类型放在单独的代码文件下**GeneratedCode**文件夹。  

- 如果 UML 类型包含在包中，则将生成的 C# 类型置于一个命名空间中，并在具有与命名空间相同的名称的文件夹中生成文件。  

- 为 UML 类的每个 `Attribute` 生成一个 C# 属性。  

- 为 UML 类型的每个 `Operation` 生成一个 C# 方法。  

- 为类参与的每个可导航关联生成一个 C# 字段。  

  通过向每个 UML 类型添加一个构造型，可以控制生成的 C# 类型的更多属性。  

|**若要创建此 C# 类型**|**绘制此 UML 类型**|**应用此构造型**|  
|---------------------------------|----------------------------|-------------------------------|  
|类|类|\<none > 或<br /><br /> C# class|  
|接口|接口|\<none > 或<br /><br /> C# interface|  
|枚举|枚举|\<none > 或<br /><br /> C# enum|  
|委托|类|C# delegate|  
|结构|类|C# struct|  

#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>在类型或其他元素上设置构造型  

1. 打开关系图上或在该元素的快捷菜单**UML 模型资源管理器**，然后选择**属性**。  

2. 在中**属性**窗口中，选择中的下拉箭头**构造型**属性，并选择你想要应用的构造型的复选框。  

   > [!TIP]
   > 如果未出现 C# 构造型，则为模型或包含你感兴趣的模型元素的包启用 C# 配置文件。 选择包或模型中的根**UML 模型资源管理器**。 然后在**属性**窗口中，选择**配置文件**，然后启用 C# 配置文件。  

3. 展开**构造型**属性以查看可设置的其他属性。  

   **描述**的类型、 属性、 操作和关联的属性写入到`<summary>`中生成的代码的注释。 将链接到类型的注释元素写入 `<remarks>` 注释。  

## <a name="varying-the-generated-code"></a>改变生成的代码  
 生成的代码随每个类型、特性或操作的属性的不同而不同。 例如，如果您设置**Is Abstract**属性的类为 true，则`abstract`关键字将出现在生成的类。 如果您设置**多重性**属性的 * * 0..\\则生成的属性将具有`IEnumerable<>`类型。  

 另外，每个构造型提供了多个可设置的附加属性。 这些值将转换为 C# 代码中的相应关键字。 例如，如果你在类上设置属性 `Is Static`，则 C# 类将为 `static`。  

 若要设置这些附加属性，请在关系图中选择该类或其他元素。 在属性窗口中，展开**构造型**，然后展开 C# 构造型，如**C# 类**。  对于类，这些附加属性包括：  

- CLR Attributes  

- Is Partial  

- Is Static  

- Is Unsafe  

- Package Visibility  

  每个特性和操作还包含可设置的构造型属性。 如果您没有看到属性的新特性上，运行**生成代码**。  

## <a name="custom"></a> 自定义生成代码命令  
 **生成代码**命令通过将转换你使用的一组文本模板的模型元素的工作原理。 有关文本模板的详细信息，请参阅[代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)。  

 模板中的一组指定*文本模板绑定*。 文本模板绑定指定应该应用哪些模板，应放置生成的输出的位置，和其他参数**生成代码**命令。  

 当你首次运行**生成代码**命令对特定模型，它将一组默认的模板绑定附加到模型的根。 这些绑定应用于模型中的所有元素。  

 但是，可以通过将你自己的绑定附加到包、类或其他元素来替代和添加到这些默认绑定。 绑定应用于它将附加到的元素内包含的所有元素。 例如，如果你希望通过一组不同的模板来转换某个特定包内的所有类型，或将这些类型输出到其他文件夹，则可将模板绑定附加到包。  

 若要检查附加到模型元素的模板绑定，请选择省略号 **[...]** 中**文本模板绑定**属性窗口中的属性。  

 **生成代码**命令将模板应用于您选择每个模型元素。 对于每个元素，应用的模板集是附加到其容器（直至并包括模型的根）的模板的组合集。  

 如果此集中的两个模板绑定都具有相同的名称，则小型容器中的绑定将替代大型容器中的绑定。 例如，模型根包含具有名称绑定**类模板**。 若要让模板应用于特定包的内容，定义自己的模板绑定具有名称**类模板**。  

 可将多个模板应用于一个模型元素。 可从每个模型元素中生成多个文件。  

> [!NOTE]
> 附加到模型的根的绑定将充当模型中所有元素的默认值。 若要查看这些默认绑定，请打开**UML 模型资源管理器**。 打开建模项目的快捷菜单，然后选择**设置代码生成**。 或者，在“UML 模型资源管理器”中选择模型的根。 在属性窗口中，选择 **[...]** 中**文本模板绑定**属性。 直到您使用的绑定将不会出现**生成代码**至少一次命令。 无法将模板绑定附加到关系图。  

#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>将文本模板绑定附加到包或其他模型元素  

1. 在中**UML 模型资源管理器**，打开模型元素的快捷菜单，然后选择**属性**。 通常，你会将文本模板绑定附加到包或模型的根。  

2. 在中**属性**窗口中，选择省略号按钮 (**[...]**) 中**文本模板绑定**属性。  

    **文本模板绑定**对话框随即出现。  

3. 选择**添加**若要创建新的文本模板绑定。  

    \- 或 -  

    选择现有绑定以对其进行编辑。  

    每个模板绑定均定义了将指定模板应用于所选模型元素以及它包含的其他模型元素的方式。  

4. 在该对话框中，设置文本模板绑定的属性。  

   |    **Property**    |                                                                                                                                                                                                                                                                                                                    **说明**                                                                                                                                                                                                                                                                                                                    |
   |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        名称        |                                                                                                                                                                                                                                                  此绑定的名称。 若要替代继承自包含包或模型的某个绑定，请使用与要替代的绑定相同的名称。                                                                                                                                                                                                                                                  |
   |     Overwrite      |                                                                                                                                                                                                                                                                                                      如果为 True，则替代任何现有代码。                                                                                                                                                                                                                                                                                                       |
   |    Target Name     | 生成的文件的名称。<br /><br /> 您可以将表达式插入此字符串等`{Name}`或`{Owner.Name}`。 例如，可以编写： `{Owner.Name}_{Name}`。 在模型元素上计算表达式。 它可使用元素而非方法的属性。 若要查找可以使用哪些属性，请查看中类型的属性 **Microsoft.VisualStudio.Uml。\\***.\*\*重要说明：* \* `{Name}`或`{Owner.Name}`可以仅在使用**目标名称**属性。 若要更改生成的类的名称，你必须修改模板。 有关详细信息，请参阅[编写文本模板](#writing)。 |
   |    项目路径    |                                                                      指定将包含转换的输出文件的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 项目的路径。 使用类型值创建新项目。 选择省略号按钮 (**[...]**) 若要选择一个现有项目。<br /><br /> 如果新项目不存在，则将创建它。 它将是一个 C# 类库项目。<br /><br /> 为此，你必须直接键入该项目。 可以包含环境变量宏，例如 %ProgramFiles% 或 %LocalAppData%。                                                                       |
   |  目标目录  |                                                                                          在其中生成目标文件的文件夹。 该路径是项目文件夹的相对路径。<br /><br /> 可以使用 `{PackageStructure}` 表达式插入与包含程序包的名称相对应的路径。 默认值为 `\GeneratedCode\{PackageStructure}`。 还可以包含环境变量，例如 %TEMP% 或 %HomePath%。 **重要说明：** `{PackageStructure}`可以仅在使用**目标目录**属性。                                                                                          |
   | 模板文件路径 |                                                                                                                                                           将执行转换的模板。<br /><br /> 可以使用提供的模板或创建你自己的模板。 可在以下位置找到提供的模板：<br /><br /> …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\                                                                                                                                                           |

5. 可将所需数量的绑定附加到一个元素。  

## <a name="writing"></a> 编写文本模板  
 可编写你自己的文本模板。 文本模板可生成程序代码或任何其他类别的文本文件。  

 建议你首先修改标准模板的副本。 可从以下位置复制模板：  

 …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\  

 若要了解文本模板，请参考以下主题。  

- 文本模板是生成的文件的原型，它包含生成的文本和读取模型的程序代码。 有关详细信息，请参阅[代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)。  

- 若要在程序代码中导航 UML 模型，你必须使用 UML API。 有关详细信息，请参阅[导航 UML 模型](../modeling/navigate-the-uml-model.md)并[UML 建模扩展性的 API 参考](../modeling/api-reference-for-uml-modeling-extensibility.md)。  

  若要使用的模板**生成代码**命令时，必须包含 Modeling 指令。 例如：  

  `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`  

  `ElementType` 特性定义了此模板将应用于的 UML 元素的类型。  

  在模板中，`this` 属于具有以下属性的临时类：  

- `Element` 为模板要应用于的 UML <xref:Microsoft.VisualStudio.Uml.Classes.IElement>。  

- `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>  

- `Host`: <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  

- `ModelBus`: <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>。 有关详细信息，请参阅[与其他模型和工具集成 UML 模型](../modeling/integrate-uml-models-with-other-models-and-tools.md)。  

- `ProfileName` =“C#Profile”  

- `ServiceProvider`: <xref:System.IServiceProvider>  

- `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>。  

- `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>。 这是在其上实现 UML ModelStore 的可视化和建模 SDK 存储。 若要获取 UML <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore>，请使用 `this.Element.GetModelStore()`。  

  当你编写文本模板时，你可能会发现以下几点很有用。 中详细描述了此信息[代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)。  

- 可在 `Output` 指令中设置结果的文件扩展名。 每个文本模板中需要一个 `Output` 指令。  

- 模板将自动引用某些程序集。 例如，这些程序集包括 System.dll 和 Microsoft.VisualStudio.Uml.Interfaces.dll。  

   若要在生成的程序代码中使用其他程序集，你必须使用 `Assembly` 指令。 例如：  

   `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`  

- 一些命名空间（例如，`System`）会自动导入你的程序代码。 对于其他命名空间，可以按使用 `Import` 语句的方式来使用 `using` 指令。 例如：  

   `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`  

   `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`  

- 使用 `Include` 指令以引用其他文件的文本。  

- 用方括号括起来的模板部分`<# ... #>`由执行**生成代码**命令。 括号外部的模板部分将复制到结果文件。 区分生成的代码和生成的文本很重要。 生成的文本可采用任何语言。  

- 计算 `<#= Expressions #>` 并将其转换为字符串。  

## <a name="see-also"></a>请参阅  
 [UML 类关系图：引用](../modeling/uml-class-diagrams-reference.md)   
 [UML 类关系图：指导原则](../modeling/uml-class-diagrams-guidelines.md)   
 [从 UML 模型生成文件](../modeling/generate-files-from-a-uml-model.md)
