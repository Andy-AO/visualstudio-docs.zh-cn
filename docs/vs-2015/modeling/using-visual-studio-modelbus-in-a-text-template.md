---
title: 在文本模板中使用 ModelBus |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9ed19a280f791fa857ffbf00ba25aa18c490aa65
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069049"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>在文本模板中使用 Visual Studio ModelBus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您编写读取模型包含的文本模板[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ModelBus 引用，你可能想要解析对访问目标模型的引用。 在这种情况下，您需要调整文本模板和引用特定于域的语言 (Dsl):

- 引用目标 DSL 必须具有配置为从文本模板访问 ModelBus 适配器。 如果你还可以从其他代码访问 DSL，除了标准的 ModelBus 适配器需要重新配置的适配器。

     适配器管理器必须继承自<xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>必须具有属性和`[HostSpecific(HostName)]`。

- 模板必须继承自<xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>。

> [!NOTE]
>  如果你想要读取 DSL 模型中不包含 ModelBus 引用，可以使用在你的 DSL 项目中生成的指令处理器。 有关详细信息，请参阅[从文本模板访问模型](../modeling/accessing-models-from-text-templates.md)。

 有关文本模板的详细信息，请参阅[使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。

## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>为从文本模板访问创建模型总线适配器
 若要解决文本模板中的 ModelBus 引用，目标 DSL 必须具有兼容的适配器。 在单独的 AppDomain 中执行文本模板[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]文档编辑器，因此适配器必须加载而不是通过 DTE 访问模型。

#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>若要创建文本模板与兼容的 ModelBus 适配器

1. 如果目标 DSL 解决方案不具有**ModelBusAdapter**项目中，创建一个使用 Modelbus 扩展向导：

    1. 下载并安装[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ModelBus 扩展，如果尚未这样做。 有关详细信息，请参阅[可视化和建模 SDK](http://go.microsoft.com/fwlink/?LinkID=185579)。

    2. 打开 DSL 定义文件。 右键单击设计图面，然后单击**启用 Modelbus**。

    3. 在对话框中，选择**我想要向 ModelBus 公开此 DSL**。 如果希望此 DSL 同时公开其模型和使用对其他 Dsl 的引用，可以选择这两个选项。

    4. 单击 **“确定”**。 新项目“ModelBusAdapter”随即添加到 DSL 解决方案中。

    5. 单击**转换所有模板**。

    6. 重新生成解决方案。

2. 如果你想要访问 DSL，从文本模板和其他代码，例如命令，重复**ModelBusAdapter**项目：

    1. 在 Windows 资源管理器，复制并粘贴所在的文件夹**ModelBusAdapter.csproj**。

    2. 重命名项目文件 (例如，若**T4ModelBusAdapter.csproj**)。

    3. 在中**解决方案资源管理器**，右键单击解决方案节点，指向**添加**，然后单击**现有项目**。 找到新的适配器项目中， **T4ModelBusAdapter.csproj**。

    4. 在每个`*.tt`文件的新项目的更改的命名空间。

    5. 右键单击解决方案资源管理器中的新项目，然后单击属性。 在属性编辑器中，更改生成的程序集和默认命名空间的名称。

    6. 在 DslPackage 项目中，添加对新的适配器项目的引用，以便它具有对这两个适配器的引用。

    7. DslPackage\source.extension.tt，在添加引用你的新适配器项目的行。

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **转换所有模板**重新生成解决方案。 应不发生任何生成错误。

3. 在新的适配器项目中，添加对以下程序集的引用：

    - Microsoft.VisualStudio.TextTemplating.11.0

         Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4. 在 AdapterManager.tt:

    - 将 AdapterManagerBase 的声明更改，以便它继承<xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>。

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - 在文件末尾附近时替换之前的 AdapterManager 类 HostSpecific 特性。 删除以下行：

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         插入以下行：

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         此属性筛选器的适配器搜索 modelbus 使用者时可用的适配器集。

5. **转换所有模板**重新生成解决方案。 应不发生任何生成错误。

## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>编写文本模板可以解析 ModelBus 引用
 通常情况下，在开始使用模板来读取和生成文件从"source"DSL。 此模板使用要读取源模型文件中所述的方式中的源 DSL 项目中生成的指令[从文本模板访问模型](../modeling/accessing-models-from-text-templates.md)。 但是，源 DSL 包含对"目标"DSL 的 ModelBus 引用。 因此想要启用用于解析引用和访问目标 DSL 的模板代码。 因此必须通过执行以下步骤来适应模板：

- 更改到模板的基本类<xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>。

- 包括`hostspecific="true"`模板指令中。

- 将程序集引用添加到目标 DSL 和其适配器，并启用 ModelBus。

- 不需要作为目标 DSL 的一部分生成的指令。

```
<#@ template debug="true" hostspecific="true" language="C#"
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
<#@ output extension=".txt" #>
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>
<#@ assembly name = "System.Core" #>
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
<#@ import namespace="Company.TargetDsl" #>
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>
<#@ import namespace="System.Linq" #>
<#
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.
  // In the source DSL Definition, the root element has a model reference:
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)
  {if (adapter != null)
   {
      // Get the root of the target model:
      TargetRoot target = adapter.ModelRoot;
    // The source DSL Definition has a class "SourceElement" embedded under the root.
    // (Let’s assume they’re all in the same model file):
    foreach (SourceElement sourceElement in source.Elements)
    {
      // In the source DSL Definition, each SourceElement has a MBR property:
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;
      // Resolve the target model element:
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);
#>
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.
<#
    }
  }}
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename
  // from a path that is relative to the text template.
#>

```

 执行此文本模板时，`SourceDsl`指令将文件加载`Sample.source`。 在模板可以访问该模型中，从开始的元素`this.ModelRoot`。 代码可以使用的域类和属性的 DSL。

 此外，该模板可以解析 ModelBus 引用。 其中的引用指向目标模型时，程序集指令让使用的域类和该模型的 DSL 的属性的代码。

- 如果不使用生成的 DSL 项目的指令，还应包括以下。

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- 使用`this.ModelBus`以获取向 ModelBus 的访问权限。

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>演练：测试使用 ModelBus 的文本模板
 在本演练中，您将执行以下步骤：

1. 构造两个 Dsl。 一个 DSL*使用者*，具有`ModelBusReference`属性，可以对其他 DSL，请参阅*提供程序*。

2. 在提供程序中创建两个 ModelBus 适配器： 一个用于通过文本模板访问另一个用于普通代码。

3. 在单个试验性项目中创建 Dsl 实例的模型。

4. 在一个模型，以指向另一个模型中设置域属性。

5. 编写将打开指向模型的双击处理程序。

6. 编写文本模板，可以加载的第一个模型，按照对其他模型，引用并读取其他模型。

#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>构造 DSL 的 ModelBus 均可访问

1. 创建新 DSL 解决方案。 对于此示例中，选择任务流解决方案模板。 将语言名称设置为`MBProvider`和文件扩展名为".provide"。

2. 在 DSL 定义关系图中，右键单击顶部附近，不是关系图的空白部分，然后单击**启用 Modelbus**。

   - 如果没有看到**启用 Modelbus**，必须下载并安装 VMSDK ModelBus 扩展。 VMSDK 网站上找到它：[可视化和建模 SDK](http://go.microsoft.com/fwlink/?LinkID=185579)。

3. 在中**启用 Modelbus**对话框中，选择**向 ModelBus 公开此 DSL**，然后单击**确定**。

    一个新项目， `ModelBusAdapter`，添加到解决方案。

   现可由 ModelBus 通过文本模板访问 DSL。 可以在命令、 事件处理程序或规则，所有这些模型文件编辑器的 AppDomain 中运行的代码中解析对它的引用。 但是，文本模板在单独的 AppDomain 中运行，并且正在编辑的情况下无法访问模型。 如果你想要访问从文本模板对此 DSL 的 ModelBus 引用，必须具有单独的 ModelBusAdapter。

#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>若要创建文本模板的配置的 ModelBus 适配器

1. 在 Windows 资源管理器，复制并粘贴 ModelBusAdapter.csproj 所在的文件夹。

    文件夹 T4ModelBusAdapter 命名。

    项目文件 T4ModelBusAdapter.csproj 重命名。

2. 在解决方案资源管理器，将添加到 MBProvider 解决方案的 T4ModelBusAdapter。 右键单击解决方案节点，指向**外**，然后单击**现有项目**。

3. 右键单击 T4ModelBusAdapter 项目节点，然后单击属性。 在项目属性窗口中更改**程序集名称**并**Default Namespace**到`Company.MBProvider.T4ModelBusAdapters`。

4. 在每个 *.tt 文件中 T4ModelBusAdapter，插入"T4"命名空间的最后一个部分，使行类似于以下。

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. 在中`DslPackage`项目中，添加到项目引用`T4ModelBusAdapter`。

6. 在 DslPackage\source.extension.tt，添加以下行下的`<Content>`。

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. 在`T4ModelBusAdapter`项目中，添加对的引用：**Microsoft.VisualStudio.TextTemplating.Modeling.11.0**

8. 打开 T4ModelBusAdapter\AdapterManager.tt:

   1. 将 AdapterManagerBase 的基类更改为 <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>。 该文件的此部分现在如下所示。

       ```
       namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters
       {
           /// <summary>
           /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer
           /// </summary>
           public partial class <#= dslName #>AdapterManagerBase
           : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager
           {

       ```

   2. 在文件末尾附近插入了以下附加特性类 AdapterManager 的前面。

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        结果如下所示。

       ```
       /// <summary>
       /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter
       /// </summary>
       [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]
       [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]
       [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]
       [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]
       public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase
       {
       }

       ```

9. 单击**转换所有模板**在标题栏的解决方案资源管理器。

10. 重新生成解决方案。 单击 F5。

11. 验证通过按 F5 的 DSL 正常工作。 在实验性的项目中，打开`Sample.provider`。 关闭 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的实验实例。

    在文本模板中以及在普通代码中，现在可以解决对此 DSL 的 ModelBus 引用。

#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>构造 DSL 使用 ModelBus 引用域属性

1. 使用最小语言解决方案模板创建新的 DSL。 命名 MBConsumer 的语言，并将设置为".consume"的文件扩展名。

2. 在 DSL 项目中，添加 MBProvider DSL 程序集的引用。 右键单击`MBConsumer\Dsl\References`，然后单击**添加引用**。 在中**浏览**选项卡上，找到 `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    这使您可以创建使用其他 DSL 的代码。 如果你想要创建对多个 Dsl 的引用，则还应添加它们。

3. 在 DSL 定义关系图中，右键单击关系图，然后单击**启用 ModelBus**。 在对话框中，选择**启用此 DSL 使用 ModelBus**。

4. 在类中`ExampleElement`，添加一个新的域属性`MBR`，并在属性窗口中将其类型设置为`ModelBusReference`。

5. 右键单击关系图上的域属性，然后单击**编辑 ModelBusReference 特定属性**。 在对话框中，选择**模型元素**。

    设置为以下文件对话框筛选器。

    `Provider File|*.provide`

    后的子字符串"&#124;"是文件选择对话框中的筛选器。 您无法将其设置为允许的任何文件使用 *。\*

    在中**模型元素类型**列表中，在提供程序 (例如，Company.MBProvider.Task) DSL 中输入的一个或多个域类的名称。 它们可以是抽象类。 如果列表为空，则用户可以设置对任何元素的引用。

6. 关闭对话框并**转换所有模板**。

   您已创建可以包含对在另一个 DSL 的元素的引用的 DSL。

#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>在解决方案中创建对另一个文件的 ModelBus 引用

1. 在 MBConsumer 解决方案中，按 CTRL + F5。 实验实例[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中打开**MBConsumer\Debugging**项目。

2. 添加一份到 Sample.provide **MBConsumer\Debugging**项目。 这是必需的因为 ModelBus 引用必须引用同一解决方案中的文件。

   1. 右键单击调试项目，指向**外**，然后单击**现有项**。

   2. 在中**添加项**对话框中，将筛选器设置为**的所有文件 (\*。\*)**.

   3. 导航到`MBProvider\Debugging\Sample.provide`，然后单击**添加**。

3. 打开 `Sample.consume`。

4. 单击一个示例形状，然后在属性窗口中，单击 **[...]** MBR 属性中。 在对话框中，单击**浏览**，然后选择`Sample.provide`。 在元素窗口中，展开类型任务并选择元素之一。

5. 保存该文件。

    (不要关闭的实验实例[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。)

   您已创建包含另一个模型中元素的 ModelBus 引用的模型。

#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>解决文本模板中的 ModelBus 引用

1. 在实验实例中的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，打开示例文本模板文件。 按如下所示设置其内容。

    ```
    <#@ template debug="true" hostspecific="true" language="C#"
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>
    <#@ output extension=".txt" #>
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
    <#@ import namespace="Company.MBProvider" #>
    <#
      // Property provided by the Consumer directive processor:
      ExampleModel consumerModel = this.ExampleModel;
      // Iterate through Consumer model, listing the elements:
      foreach (ExampleElement element in consumerModel.Elements)
      {
    #>
       <#= element.Name #>
    <#
        if (element.MBR != null)
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))
      {
              // If we allowed multiple types or DSLs in the MBR, discover type here.
        Task task = adapter.ResolveElementReference<Task>(element.MBR);
    #>
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>
    <#
          }
      }
    #>

    ```

     请注意以下内容：

    1. `hostSpecific`并`inherits`的属性`template`指令必须设置。

    2. 使用者模型访问以通常的方式，通过在该 DSL 中生成的指令处理器。

    3. 程序集并导入指令必须能够访问 ModelBus 和 DSL 的提供程序的类型。

    4. 如果您知道很多 Mbr 已链接到相同的模型，则最好调用 CreateAdapter 仅一次。

2. 保存模板。 验证生成的文本文件类似于以下。

    ```

    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2

    ```

#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>解决在笔势处理程序中的 ModelBus 引用

1. 关闭实验实例的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，如果它正在运行。

2. 添加内容的名为 MBConsumer\Dsl\Custom.cs 并将其内容设置为以下文件。

    ```

    namespace Company.MB2Consume
    {
      using Microsoft.VisualStudio.Modeling.Integration;
      using Company.MB3Provider;

      public partial class ExampleShape
      {
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)
        {
          base.OnDoubleClick(e);
          ExampleElement element = this.ModelElement as ExampleElement;
          if (element.MBR != null)
          {
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))
            {
              Task task = adapter.ResolveElementReference<Task>(element.MBR);
              // Open a window on this model:
              ModelBusView view = adapter.GetDefaultView();
              view.Show();
              view.SetSelection(element.MBR);
            }
          }
        }
      }
    }

    ```

3. 按 Ctrl+F5。

4. 在实验实例中的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，打开`Debugging\Sample.consume`。

5. 双击一个形状。

     如果该元素上设置了 MBR，被引用的模型将打开，并且所选引用的元素。

## <a name="see-also"></a>请参阅
 [使用 Visual Studio Modelbus 集成模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)[代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)
