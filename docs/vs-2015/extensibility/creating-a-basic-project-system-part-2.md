---
title: 创建基本项目系统，第 2 部分 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b4709cc5f011dd55445583c46dd96894b979647c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435555"
---
# <a name="creating-a-basic-project-system-part-2"></a>创建基本项目系统，第 2 部分
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在此系列中，在第一个演练[创建基本项目系统，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)，演示如何创建基本项目系统。 本演练中的基础上基本项目系统添加 Visual Studio 模板、 属性页中和其他功能。 在开始此之前，必须完成第一个演练。  
  
 本演练介绍了如何创建具有项目文件名称扩展.myproj 的项目类型。 若要完成本演练，您无需创建您自己的语言，因为本演练中继承现有的 Visual C# 项目系统中。  
  
 本演练介绍了如何完成这些任务：  
  
- 创建 Visual Studio 模板。  
  
- 部署 Visual Studio 模板。  
  
- 创建项目类型的子节点，在**新的项目**对话框。  
  
- 启用 Visual Studio 模板中的参数替换。  
  
- 创建的项目属性页。  
  
> [!NOTE]
> 在本演练中的步骤基于 C# 项目。 但是，除了如文件扩展名和代码的详细信息，可以使用相同的步骤对于 Visual Basic 项目。  
  
## <a name="creating-a-visual-studio-template"></a>创建 Visual Studio 模板  
 [创建基本项目系统，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)演示如何创建基本项目模板，并将其添加到项目系统。 它还演示如何通过 Visual Studio 注册此模板使用<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>属性，它在系统注册表中写入 \Templates\Projects\SimpleProject\ 文件夹的完整路径。  
  
 通过使用 Visual Studio 模板 （.vstemplate 文件） 而不基本的项目模板，可以控制模板中的显示方式**新的项目**对话框和如何替换模板参数。  .Vstemplate 文件是一个 XML 文件，描述源代码文件的方式使用项目系统模板创建项目时将包括在内。 项目系统本身是通过收集.vstemplate 文件并在.zip 文件中，源文件构建和部署通过将.zip 文件复制到 Visual Studio 可被识别的位置。 在本演练后面的更详细地说明了此过程。  
  
1. 在中[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，打开按照创建 SimpleProject 解决方案[创建基本项目系统，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)。  
  
2. 在 SimpleProjectPackage.cs 文件中，找到 ProvideProjectFactory 属性。 将为 null，第二个参数 （项目名称） 和第四个参数 （项目模板文件夹的路径） 替换为"。\\\NullPath"，按如下所示。  
  
   ```  
   [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
       ".\\NullPath",  
   LanguageVsTemplate = "SimpleProject")]  
   ```  
  
3. 将添加到 \Templates\Projects\SimpleProject\ 文件夹名 SimpleProject.vstemplate 的 XML 文件。  
  
4. 将以下代码替换为 SimpleProject.vstemplate 的内容。  
  
   ```xml  
   <VSTemplate Version="2.0.0" Type="Project"  
       xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
     <TemplateData>  
       <Name>SimpleProject Application</Name>  
       <Description>  
           A project for creating a SimpleProject application  
        </Description>  
        <Icon>SimpleProject.ico</Icon>  
        <ProjectType>SimpleProject</ProjectType>  
     </TemplateData>  
     <TemplateContent>  
       <Project File="SimpleProject.myproj" ReplaceParameters="true">  
         <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
             Program.cs  
         </ProjectItem>  
         <ProjectItem ReplaceParameters="true" OpenInEditor="false">  
            AssemblyInfo.cs  
         </ProjectItem>  
       </Project>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
5. 在中**属性**窗口中，选择所有五个文件中的 \Templates\Projects\SimpleProject\ 文件夹并设置**生成操作**到**ZipProject**。  
  
   ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
   \<TemplateData > 部分确定位置和 SimpleProject 项目类型中的外观**新建项目**对话框中的，按如下所示：  
  
- \<名称 > 元素命名为 SimpleProject 的应用程序的项目模板。  
  
- \<说明 > 元素包含在显示的说明**新建项目**对话框中选择项目模板时。  
  
- \<图标 > 元素指定与 SimpleProject 项目类型一起显示的图标。  
  
- \<ProjectType > 元素中的项目类型命名**新建项目**对话框。 此名称将替换 ProvideProjectFactory 属性的项目名称参数。  
  
  > [!NOTE]
  > \<ProjectType > 元素必须匹配`LanguageVsTemplate`自变量的`ProvideProjectFactory`SimpleProjectPackage.cs 文件中的属性。  
  
  \<TemplateContent > 部分介绍了创建新项目时，将生成这些文件：  
  
- SimpleProject.myproj  
  
- Program.cs  
  
- AssemblyInfo.cs  
  
  所有三个文件都有`ReplaceParameters`设置为 true，启用参数替换。  Program.cs 文件具有`OpenInEditor`设置为 true，这会导致要创建的项目时在代码编辑器中打开的文件。  
  
  有关 Visual Studio 模板架构中的元素的详细信息，请参阅[Visual Studio 模板架构引用](../extensibility/visual-studio-template-schema-reference.md)。  
  
> [!NOTE]
> 如果项目具有多个 Visual Studio 模板，每个模板是在单独的文件夹。 在该文件夹中的每个文件必须具有**生成操作**设置为**ZipProject**。  
  
## <a name="adding-a-minimal-vsct-file"></a>添加最小.vsct 文件  
 Visual Studio 必须以识别新的或修改 Visual Studio 模板模式下安装程序在运行。 模式下安装程序需要.vsct 文件必须存在。 因此，必须将最小.vsct 文件添加到项目。  
  
1. 将添加到 SimpleProject 项目名 SimpleProject.vsct 的 XML 文件。  
  
2. 将以下代码替换为 SimpleProject.vsct 文件的内容。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3. 设置**生成操作**到此文件**VSCTCompile**。 您可以执行此操作仅在.csproj 文件中，不能在**属性**窗口。 请确保**生成操作**此文件设置为**None**此时。  
  
    1. 右键单击 SimpleProject 节点，然后单击**编辑 SimpleProject.csproj**。  
  
    2. 在.csproj 文件中，找到 SimpleProject.vsct 的项目。  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3. 将生成操作更改**VSCTCompile**。  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4. 将项目文件和关闭编辑器。  
  
    5. 保存 SimpleProject 节点，然后在**解决方案资源管理器**单击**重新加载项目**。  
  
## <a name="examining-the-visual-studio-template-build-steps"></a>检查 Visual Studio 模板生成步骤  
 VSPackage 项目生成系统.vstemplate 文件发生更改或重新生成包含.vstemplate 文件的项目时，通常将 Visual Studio 运行模式下安装程序中。 通过将 MSBuild 的详细级别设置为 Normal 或更高版本，您可以照着操作。  
  
1. 在 **“工具”** 菜单上，单击 **“选项”**。  
  
2. 展开**项目和解决方案**节点，并选择**生成并运行**。  
  
3. 设置**MSBuild 项目生成输出详细信息**到**正常**。 单击 **“确定”**。  
  
4. 重新生成 SimpleProject 项目。  
  
   生成步骤来创建.zip 项目文件应类似于下面的示例。  
  
```  
ZipProjects:  
1>  Zipping ProjectTemplates  
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".  
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip  
1>ZipItems:  
1>  Zipping ItemTemplates  
1>  SimpleProject ->  
```  
  
## <a name="deploying-a-visual-studio-template"></a>部署 Visual Studio 模板  
 Visual Studio 模板不包含路径信息。 因此，必须将模板.zip 文件部署到 Visual Studio 可被识别的位置。 ProjectTemplates 文件夹的位置通常是 **\<%LOCALAPPDATA%> \Microsoft\VisualStudio\14.0Exp\ProjectTemplates**。  
  
 若要部署项目工厂，安装程序必须具有管理员权限。 它将部署模板的 Visual Studio 安装节点下： **...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates**。  
  
## <a name="testing-a-visual-studio-template"></a>测试 Visual Studio 模板  
 测试您的项目工厂以查看是否它通过使用 Visual Studio 模板创建项目层次结构。  
  
1. 重置 Visual Studio SDK 实验实例。  
  
    在[!INCLUDE[win7](../includes/win7-md.md)]:在开始菜单中，找到**Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools**文件夹，，然后选择**重置 Microsoft Visual Studio 实验实例**。  
  
    更高版本的 Windows:在开始屏幕上键入**重置 Microsoft Visual Studio\<版本 > 实验实例**。  
  
2. 显示命令提示符窗口。 当看到单词`Press any key to continue`，单击 ENTER。 在窗口关闭后，打开 Visual Studio。  
  
3. 重新生成 SimpleProject 项目并启动调试。 将显示在实验实例。  
  
4. 在实验实例中，将创建 SimpleProject 项目。 在中**新的项目**对话框中，选择**SimpleProject**。  
  
5. 应会看到 SimpleProject 的新实例。  
  
   ![](../extensibility/media/simpproj2-newproj.png "SimpProj2_NewProj")  
  
   ![](../extensibility/media/simpproj2-myproj.png "SimpProj2_MyProj")  
  
## <a name="creating-a-project-type-child-node"></a>创建一个项目类型的子节点  
 可以将一个子节点添加到中的项目类型节点**新的项目**对话框。  例如，对于 SimpleProject 项目类型，可能具有控制台应用程序、 窗口应用程序、 web 应用程序等的子的节点。  
  
 通过更改项目文件并添加创建子节点\<OutputSubPath > 孩子们接触到\<ZipProject > 元素。 在生成或部署过程中复制模板时，每一个子节点将成为项目模板文件夹的子文件夹。  
  
 本部分演示如何创建一个控制台中的子节点 SimpleProject 项目类型。  
  
1. \Templates\Projects\SimpleProject\ 文件夹重命名为 \Templates\Projects\ConsoleApp\\。  
  
2. 在中**属性**窗口中，选择 \Templates\Projects\ConsoleApp\ 文件夹中的所有五个文件，并确保**生成操作**设置为**ZipProject**。  
  
3. 在 SimpleProject.vstemplate 文件中，添加以下行的末尾\<TemplateData > 部分中的，只需在结束标记。  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     这将导致才会出现在控制台中的子节点和 SimpleProject 父节点，这是子节点的上一级别中的控制台应用程序模板。  
  
4. 保存 SimpleProject.vstemplate 文件。  
  
5. 在.csproj 文件中，添加\<OutputSubPath > 到每个 ZipProject 元素。 卸载项目，与之前一样，并编辑项目文件。  
  
6. 找到\<ZipProject > 元素。 每个\<ZipProject > 元素中，添加\<OutputSubPath > 元素并为其提供值控制台。 ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>  
    ```  
  
7. 添加此\<PropertyGroup > 的项目文件：  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8. 保存项目文件并重新加载项目。  
  
## <a name="testing-the-project-type-child-node"></a>测试项目类型的子节点  
 测试已修改的项目文件以查看是否**控制台**子节点显示在**新项目**对话框。  
  
1. 运行**重置 Microsoft Visual Studio 实验实例**工具。  
  
2. 重新生成 SimpleProject 项目并启动调试。 应显示在实验实例  
  
3. 在中**新的项目**对话框中，单击**SimpleProject**节点。 **控制台应用程序**模板应出现在**模板**窗格。  
  
4. 展开**SimpleProject**节点。 **控制台**应显示子节点。 **SimpleProject 应用程序**模板仍会显示在**模板**窗格。  
  
5. . 单击**取消**和停止调试  
  
   ![](../extensibility/media/simpproj2-rollup.png "SimpProj2_Rollup")  
  
   ![](../extensibility/media/simpproj2-subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substituting-project-template-parameters"></a>替换项目模板参数  
 [创建基本项目系统，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)介绍了如何覆盖`ProjectNode.AddFileFromTemplate`方法来执行一种基本类型的模板参数替换。 本部分介绍如何使用更复杂的 Visual Studio 模板参数。  
  
 当使用中的 Visual Studio 模板创建项目**新的项目**对话框中，模板参数替换为字符串以自定义项目。 模板参数是一个特殊的标记，开始和结束的美元符号，例如，$time$。 以下两个参数是用于启用基于模板的项目中的自定义特别有用：  
  
- $GUID [1-10] $ 将替换为新的 Guid。 您可以指定最多 10 个唯一的 Guid，例如，$guid1$。  
  
- $safeprojectname$ 是中的用户提供的名称**新的项目**对话框中，修改以删除所有不安全字符和空格。  
  
  有关模板参数的完整列表，请参阅[模板参数](../ide/template-parameters.md)。  如果你想要创建你自己的自定义模板参数，请参阅[NIB:如何：将自定义参数传递给模板](http://msdn.microsoft.com/5bc2ad11-84c7-4683-a276-e5e00d85d8fb)。  
  
#### <a name="to-substitute-project-template-parameters"></a>若要替换项目的模板参数  
  
1. 在 SimpleProjectNode.cs 文件中，删除`AddFileFromTemplate`方法。  
  
2. 在 \Templates\Projects\ConsoleApp\SimpleProject.myproj 文件中，找到\<根命名空间 > 属性并将其值更改为 $safeprojectname$。  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3. 在 \Templates\Projects\SimpleProject\Program.cs 文件中，文件的内容将替换为以下代码：  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace $safeprojectname$  
    {  
        [Guid("$guid1$")]  
        public class $safeprojectname$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
4. 重新生成 SimpleProject 项目并启动调试。 应显示在实验实例。  
  
5. 创建新的 SimpleProject 控制台应用程序。 (在**项目类型**窗格中，选择**SimpleProject**。 下**Visual Studio 已安装的模板**，选择**控制台应用程序**。)  
  
6. 在新建的项目中，打开 Program.cs。 它应类似于以下 （文件中的 GUID 值将有所不同。）：  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace Console_Application1  
    {  
        [Guid("00000000-0000-0000-00000000-00000000)"]  
        public class Console_Application1  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
## <a name="creating-a-project-property-page"></a>创建项目属性页  
 可以为您的项目类型创建属性页，以便用户可以查看和更改基于模板的项目中的属性。 本部分演示如何创建独立于配置的属性页。 此基本属性页使用属性网格显示在属性页类中公开的公共属性。  
  
 派生属性页类从`SettingsPage`基类。 提供的属性网格`SettingsPage`类知道大多数基元数据类型并且知道如何显示它们。  此外，`SettingsPage`类知道如何持久保存到项目文件的属性值。  
  
 在本部分中创建的属性页可以更改和保存这些项目属性：  
  
- AssemblyName  
  
- OutputType  
  
- 根命名空间。  
  
1. 在 SimpleProjectPackage.cs 文件中，添加以下`ProvideObject`属性为`SimpleProjectPackage`类：  
  
   ```  
   [ProvideObject(typeof(GeneralPropertyPage))]  
   public sealed class SimpleProjectPackage : ProjectPackage  
   ```  
  
    这将会注册属性页类`GeneralPropertyPage`com  
  
2. 在 SimpleProjectNode.cs 文件中，将添加到这两个重写的方法`SimpleProjectNode`类：  
  
   ```  
   protected override Guid[] GetConfigurationIndependentPropertyPages()  
   {  
       Guid[] result = new Guid[1];  
       result[0] = typeof(GeneralPropertyPage).GUID;  
       return result;  
   }  
   protected override Guid[] GetPriorityProjectDesignerPages()  
   {  
       Guid[] result = new Guid[1];  
       result[0] = typeof(GeneralPropertyPage).GUID;  
        return result;  
   }  
   ```  
  
    这两种方法返回的属性页 Guid 的数组。  GeneralPropertyPage GUID 是数组中的唯一元素，因此**属性页**对话框中将只显示一页。  
  
3. 添加到 SimpleProject 项目名为 GeneralPropertyPage.cs 一个类文件。  
  
4. 使用以下代码替换此文件的内容：  
  
   ```  
   using System;  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio;  
   using Microsoft.VisualStudio.Project;  
   using System.ComponentModel;  
  
   namespace SimpleProject  
   {  
       [ComVisible(true)]  
       [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]  
       public class GeneralPropertyPage : SettingsPage  
       {  
           private string assemblyName;  
           private OutputType outputType;  
           private string defaultNamespace;  
  
           public GeneralPropertyPage()  
           {  
               this.Name = "General";  
           }  
  
           [Category("AssemblyName")]  
           [DisplayName("AssemblyName")]  
           [Description("The output file holding assembly metadata.")]  
           public string AssemblyName  
           {  
               get { return this.assemblyName; }  
           }  
           [Category("Application")]  
           [DisplayName("OutputType")]  
           [Description("The type of application to build.")]  
           public OutputType OutputType  
           {  
               get { return this.outputType; }  
               set { this.outputType = value; this.IsDirty = true; }  
           }  
           [Category("Application")]  
           [DisplayName("DefaultNamespace")]  
           [Description("Specifies the default namespace for added items.")]  
           public string DefaultNamespace  
           {  
               get { return this.defaultNamespace; }  
               set { this.defaultNamespace = value; this.IsDirty = true; }  
           }  
  
           protected override void BindProperties()  
           {  
               this.assemblyName = this.ProjectMgr.GetProjectProperty(  
   "AssemblyName", true);  
               this.defaultNamespace = this.ProjectMgr.GetProjectProperty(  
   "RootNamespace", false);  
  
               string outputType = this.ProjectMgr.GetProjectProperty(  
   "OutputType", false);  
               this.outputType =   
   (OutputType)Enum.Parse(typeof(OutputType), outputType);  
           }  
  
           protected override int ApplyChanges()  
           {  
               this.ProjectMgr.SetProjectProperty(  
   "AssemblyName", this.assemblyName);  
               this.ProjectMgr.SetProjectProperty(  
   "OutputType", this.outputType.ToString());  
               this.ProjectMgr.SetProjectProperty(  
   "RootNamespace", this.defaultNamespace);  
               this.IsDirty = false;  
  
               return VSConstants.S_OK;  
           }  
       }  
   }  
   ```  
  
    `GeneralPropertyPage`类公开程序集名称、 OutputType 和根命名空间的三个公共属性。 由于程序集名称具有无设置方法，它将显示为只读属性。 OutputType 是一个枚举的常量，使其显示为下拉列表中。  
  
    `SettingsPage`基类提供了`ProjectMgr`要保持的属性。 `BindProperties`方法使用`ProjectMgr`检索保存的属性值并设置相应的属性。  `ApplyChanges`方法使用`ProjectMgr`获取属性的值并将其保存到项目文件。 该属性设置方法设置`IsDirty`为 true 以指示属性具有持久保存。  当您保存项目或解决方案时，会发生持久性服务。  
  
5. 重新生成 SimpleProject 解决方案并启动调试。 应显示在实验实例。  
  
6. 在实验实例中，将创建一个新的 SimpleProject 应用程序。  
  
7. Visual Studio 会调用您的项目工厂通过使用 Visual Studio 模板创建项目。 在代码编辑器中打开新的 Program.cs 文件。  
  
8. 右键单击项目节点中的**解决方案资源管理器**，然后单击**属性**。 随即显示“属性页”对话框。  
  
   ![](../extensibility/media/simpproj2-proppage.png "SimpProj2_PropPage")  
  
## <a name="testing-the-project-property-page"></a>测试项目属性页  
 现在可以测试是否可以修改和更改属性值。  
  
1. 在中**MyConsoleApplication 属性页**对话框中，更改**DefaultNamespace**到**MyApplication**。  
  
2. 选择**OutputType**属性，并选择**类库**。  
  
3. 单击**Apply**，然后单击**确定**。  
  
4. 重新打开**属性页**对话框框，然后验证已保存所做的更改。  
  
5. 关闭 Visual Studio 的实验实例。  
  
6. 重新打开实验实例。  
  
7. 重新打开**属性页**对话框框，然后验证已保存所做的更改。  
  
8. 关闭 Visual Studio 的实验实例。  
  
   ![](../extensibility/media/simpproj2-proppage2.png "SimpProj2_PropPage2")
