---
title: 创建软件开发工具包 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ad14712653aeca146ffe00cc5c79fd044ce2a4b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345379"
---
# <a name="create-a-software-development-kit"></a>创建软件开发工具包
软件开发工具包 (SDK) 是一系列 Api，您可以参考作为 Visual Studio 中的单个项。 **引用管理器**对话框会列出与项目相关的所有 Sdk。 向项目添加 SDK，Api 时，Visual Studio 中提供。

 有两种类型的 Sdk:

- 平台 Sdk 的开发平台的应用程序的必需组件。 例如，[!INCLUDE[win81](../debugger/includes/win81_md.md)]开发所需的 SDK[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]应用。

- 扩展 Sdk 是可选扩展平台，但不用于开发该平台的应用程序必需的组件。

  以下各节介绍的常规基础结构的 Sdk 以及如何创建的平台 SDK 和扩展 SDK。

- [平台 Sdk](#PlatformSDKs)

- [扩展 Sdk](#ExtensionSDKs)

## <a name="PlatformSDKs"></a> 平台 Sdk
 开发适用于平台的应用需要平台 Sdk。 例如，[!INCLUDE[win81](../debugger/includes/win81_md.md)]开发适用于应用程序所需的 SDK [!INCLUDE[win81](../debugger/includes/win81_md.md)]。

### <a name="installation"></a>安装
 所有平台 Sdk 将都安装在*HKLM\Software\Microsoft\Microsoft Sdk\\[TPI] \v [TPV]\\ @InstallationFolder = [SDK 根]* 。 相应地， [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK 安装在*HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*。

### <a name="layout"></a>布局
 平台 Sdk 将具有以下布局：

```
\[InstallationFolder root]
            SDKManifest.xml
            \References
                  \[config]
                        \[arch]
            \DesignTime
                  \[config]
                        \[arch]
```

| 节点 | 描述 |
|------------------------| - |
| *引用*文件夹 | 包含包含 Api，可对编码的二进制文件。 这些可能包括 Windows 元数据 (WinMD) 文件或程序集。 |
| *DesignTime*文件夹 | 包含仅在预运行/调试时所需的文件。 这些可能包括 XML 文档、 库、 标头中，工具箱设计时二进制文件、 MSBuild 项目等<br /><br /> XML 文档会理想情况下，放 *\DesignTime*文件夹中，但引用的 XML 文档将继续与 Visual Studio 中的参考文件一起放置。 例如，引用的 XML 文档<em>\References\\[配置]\\[arch]\sample.dll</em>将是 *\References\\[配置]\\[arch]\sample.xml*，并将该文档的本地化的版本 *\References\\[配置]\\[arch]\\[locale]\sample.xml*。 |
| *配置*文件夹 | 可以有只有三个文件夹：*调试*，*零售*并*CommonConfiguration*。 SDK 作者可以将其下的文件放*CommonConfiguration*如果相同的 SDK 文件集应使用，而不考虑目标 SDK 使用者配置。 |
| *体系结构*文件夹 | 任何受支持*体系结构*文件夹可以存在。 Visual Studio 支持以下体系结构： x86、 x64、 ARM 和非特定语言。 注意:Win32 映射为 x86，而 AnyCPU 映射到非特定语言。<br /><br /> MSBuild 仅查找 *\CommonConfiguration\neutral*平台 sdk。 |
| *SDKManifest.xml* | 此文件描述了 Visual Studio 应如何使用 SDK。 查看 SDK 清单[!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName：** 对象浏览器将显示在浏览列表中的值。<br /><br /> **PlatformIdentity:** 此属性存在本地告知 Visual Studio 和 MSBuild SDK 是一个平台 SDK 并且不应复制添加从它的引用。<br /><br /> **TargetFramework:** Visual Studio 使用此属性以确保，它仅投影面向此设置的值中指定的同一框架属性可以使用 SDK。<br /><br /> **MinVSVersion:** Visual Studio 使用此属性使用适用于它的 Sdk。<br /><br /> **参考：** 此属性必须指定为只有那些包含控件的引用。 有关如何指定包含控件的引用的信息，请参阅下面。 |

## <a name="ExtensionSDKs"></a> 扩展 Sdk
 以下部分介绍需要执行的操作将部署扩展 SDK。

### <a name="installation"></a>安装
 扩展 Sdk 可以无需指定注册表项为特定用户还是为所有用户安装。 若要安装适用于所有用户的 SDK，请使用以下路径：

 *%Program Files%\Microsoft Sdk\<目标平台\>\v < 平台版本号\>\ExtensionSDKs*

 对于特定于用户的安装，使用以下路径：

 *Sdk %USERPROFILE%\AppData\Local\Microsoft\<目标平台\>\v < 平台版本号\>\ExtensionSDKs*

 如果你想要使用不同的位置，必须执行两项操作之一：

1. 注册表项中指定它：

     **HKLM\Software\Microsoft\Microsoft Sdk\<目标平台 > \v < 平台版本号\>\ExtensionSDKs\<SDKName >\<SDKVersion >** \

     并添加具有值 （默认值） 子项`<path to SDK><SDKName><SDKVersion>`。

2. 添加 MSBuild 属性`SDKReferenceDirectoryRoot`到项目文件。 此属性的值是你想要引用扩展 Sdk 驻留在其中的目录的以分号分隔列表。

### <a name="installation-layout"></a>安装布局
 扩展 Sdk 具有以下安装布局：

```
\<ExtensionSDKs root>
           \<SDKName>
                 \<SDKVersion>
                        SDKManifest.xml
                        \References
                              \<config>
                                    \<arch>
                        \Redist
                              \<config>
                                    \<arch>
                        \DesignTime
                               \<config>
                                     \<arch>

```

1. \\< SDKName\>\\< SDKVersion\>： 名称和版本的扩展 SDK 派生到 SDK 根路径中对应的文件夹名称。 MSBuild 使用此标识来在磁盘上，找到 SDK 和 Visual Studio 将显示在此标识**属性**窗口和**引用管理器**对话框。

2. *引用*文件夹： 包含 Api 的二进制文件。 这些可能是 Windows 元数据 (WinMD) 文件或程序集。

3. *Redist*文件夹： 所需的运行时/调试，应获取打包为用户的应用程序的一部分的文件。 所有二进制文件应放置在下 *\redist\\< config\>\\< a c h\>* ，以及二进制名称应采用以下格式，以确保唯一性： *]* \<公司 >。\<产品 >。\<用途 >。\<扩展 ><em>。例如，*Microsoft.Cpp.Build.dll</em>。 与其他 sdk （例如，javascript、 css、 pri、 xaml、 png 和 jpg 文件） 的文件名可能发生冲突的名称的所有文件应都置于下方<em>\redist\\< config\>\\< arch\> \\< sdkname\> \*除了与 XAML 相关联的文件控制。这些文件应放置在下 * \redist\\< 配置\>\\< a c h\>\\< componentname\>\\</em>。

4. *DesignTime*文件夹： 文件在仅前的运行/调试所需的时间，不应打包为用户的应用程序的一部分。 这些可能是 XML 文档、 库、 标头中，工具箱设计时二进制文件、 MSBuild 项目等。 适用于消耗的本机项目必须进行的任何 SDK *SDKName.props*文件。 下面显示了此类型的文件的示例。

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>
       <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>
       <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>
       <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>
       <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>
       <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>
       <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>
     </PropertyGroup>
   </Project>

   ```

    引用文件旁边放置 XML 参考文档。 例如，XML 参考文档 *\References\\< config\>\\< a c h\>\sample.dll*程序集是 *\References\\< config\>\\< a c h\>\sample.xml*，并且该文档的本地化的版本 *\References\\< 配置\>\\<arch\>\\< 区域设置\>\sample.xml*。

5. *配置*文件夹： 三个子文件夹：*调试*，*零售*，和*CommonConfiguration*。 SDK 作者可以将其下的文件放*CommonConfiguration*时相同的 SDK 文件集应使用，而不考虑针对 SDK 使用者的配置。

6. *体系结构*文件夹： 支持以下体系结构： x86、 x64、 ARM，非特定语言。 Win32 映射为 x86，而 AnyCPU 映射到非特定语言。

### <a name="sdkmanifestxml"></a>SDKManifest.xml
 此文件描述了 Visual Studio 应如何使用 SDK。 下面是一个示例。

```
<FileList>
DisplayName = "My SDK"
ProductFamilyName = "My SDKs"
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"
MinVSVersion = "14.0"
MaxPlatformVersion = "8.1"
AppliesTo = "WindowsAppContainer + WindowsXAML"
SupportPrefer32Bit = "True"
SupportedArchitectures = "x86;x64;ARM"
SupportsMultipleVersions = "Error"
CopyRedistToSubDirectory = "."
DependsOn = "SDKB, version=2.0"
MoreInfo = "https://msdn.microsoft.com/MySDK">
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />
<ToolboxItems VSCategory = "Toolbox.Default" />
</File>
</FileList>
```

 以下列表提供了文件的元素。

1. DisplayName： 在引用管理器、 解决方案资源管理器、 对象浏览器和 Visual Studio 的其他位置中的用户界面中显示的值。

2. ProductFamilyName:总体 SDK 产品名称。 例如， [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK 名为"Microsoft.WinJS.1.0"和"Microsoft.WinJS.2.0"属于相同的一系列 SDK 产品系列，"Microsoft.WinJS"。 此属性允许 Visual Studio 和 MSBuild 进行连接。 如果此属性不存在，则 SDK 名称用作产品系列名称。

3. FrameworkIdentity:指定一个或多个 Windows 组件库依赖项。 此属性的值放入使用方应用程序的清单。 此属性是仅适用于 Windows 组件库。

4. TargetFramework:指定在引用管理器和工具箱中可用的 Sdk。 这是以分号分隔的目标框架名字对象，例如".NET Framework，版本 = v2.0;.NET Framework，版本 = v4.5.1"。 如果指定了多个相同的目标框架版本，引用管理器用于筛选目的使用指定的最低版本。 例如，如果".NET Framework，版本 = v2.0;.NET Framework，版本 = v4.5.1"指定，则将使用引用管理器".NET Framework，版本 = v2.0"。 如果指定特定的目标框架配置文件，则仅该配置文件将用于筛选目的使用引用管理器。 例如，当"Silverlight，版本 = v4.0，profile = WindowsPhone"指定，则引用管理器的筛选器仅在 Windows Phone 配置文件;面向完整 Silverlight 4.0 框架的项目看不到 SDK 在引用管理器。

5. MinVSVersion:最小的 Visual Studio 版本。

6. MaxPlatformVerson:最大目标平台版本应该用于指定在其扩展 SDK 不起作用的平台版本。 例如，Microsoft 视觉对象C++运行时包 v11.0 应仅由 Windows 8 项目引用。 因此，Windows 8 项目 MaxPlatformVersion 是 8.0。 这意味着引用管理器中筛选出 Microsoft VisualC++对于 Windows 8.1 项目，运行时包和 MSBuild 将引发错误时[!INCLUDE[win81](../debugger/includes/win81_md.md)]项目引用它。 注意： 此元素是从开始支持[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]。

7. AppliesTo:指定可在引用管理器中通过指定适用的 Visual Studio 项目类型的 Sdk。 识别的九个值：WindowsAppContainer、 VisualC、 VB、 CSharp、 WindowsXAML、 管理，JavaScript 和本机。 可以使用 SDK 作者和 ("+)，或 ("&#124;")，而不 ("！")若要指定完全适用于 SDK 的项目类型的作用域的运算符。

    WindowsAppContainer 标识项目类型提供的[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]应用。

8. SupportPrefer32Bit:支持的值为"True"和"False"。 默认值为"True"。 如果值设置为"False"，MSBuild 将返回的错误[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]项目 （或警告的桌面项目） 引用 SDK 的项目是否已启用的 Prefer32Bit。 有关 Prefer32Bit 详细信息，请参阅[生成页，项目设计器 (C#)](../ide/reference/build-page-project-designer-csharp.md)或[编译页，项目设计器 (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)。

9. SupportedArchitectures:以分号分隔的 SDK 支持的体系结构的列表。 如果使用的项目中的目标的 SDK 体系结构不受支持，MSBuild 将显示警告。 如果未指定此特性，MSBuild 将永远不会显示此类型的警告。

10. SupportsMultipleVersions:如果此属性设置为**错误**或**警告**，MSBuild 指示在同一个项目不能引用相同的 SDK 系列的多个版本。 如果此属性不存在或设置为**允许**，MSBuild 不会显示此类型的错误或警告。

11. AppX:指定在磁盘上的 Windows 组件库的应用程序包的路径。 本地调试期间，此值被传递给 Windows 组件库的注册组件。 文件名称的命名约定 *\<公司 >。\<产品 >。\<体系结构 >。\<配置 >。\<版本 >.appx*。 如果它们不应用于 Windows 组件库，配置和体系结构是可选的属性名称和属性值中。 此值是仅适用于 Windows 组件库。

12. CopyRedistToSubDirectory:指定的位置下的文件 *\redist*文件夹复制相对于应用程序包的根目录 (即**包位置**中选择**创建应用程序包**向导） 和运行时布局的根元素。 默认位置是应用程序包的根目录并**F5**布局。

13. DependsOn:定义此 SDK 所依赖的 Sdk 的 SDK 标识的列表。 此属性将显示在详细信息窗格中的引用管理器。

14. MoreInfo:提供帮助和的详细信息 web 页面的 URL。 在右窗格中的引用管理器的详细信息链接中使用此值。

15. 注册类型：应用程序清单中指定的 WinMD 注册，需对本机 WinMD，有一个对应的实现 DLL。

16. 文件引用：指定包含控件或本机 Winmd 的引用。 有关如何指定包含控件的引用的信息，请参阅[指定的工具箱项的位置](#ToolboxItems)下面。

## <a name="ToolboxItems"></a> 指定的工具箱项的位置
 ToolBoxItems 元素*SDKManifest.xml*架构在平台和扩展 Sdk 中指定的类别和工具箱项的位置。 以下示例演示如何指定不同的位置。 这是适用于 WinMD 或 DLL 的引用。

1. 将控件放在工具箱的默认类别。

    ```
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. 放置在特定的类别名称的控件。

    ```
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. 放置在特定类别名称的控件。

    ```
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. 在 Blend 和 Visual Studio 放置在不同的类别名称的控件。

    ```
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. 枚举以不同的方式在 Blend 和 Visual Studio 中的特定控件。

    ```
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. 枚举特定控件，并将其放置在 Visual Studio 通用路径下或仅在所有的控件组。

    ```
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. 枚举特定控件，并没有它们在 ChooseItems 中显示指定的一组要在工具箱中。

    ```
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>请参阅
- [演练：使用 SDK 创建C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [演练：创建 SDK 使用C#或 Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [管理项目中的引用](../ide/managing-references-in-a-project.md)
