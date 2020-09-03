---
title: 常用的 MSBuild 项目属性 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- msbuild, common properties
- msbuild, project file properties
- ExcludeDeploymentUrl property
- project file properties (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
caps.latest.revision: 39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1eb56d1334eb18dd5872457d032e5780a3f75eb3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698708"
---
# <a name="common-msbuild-project-properties"></a>常用的 MSBuild 项目属性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

下表列出了在 Visual Studio 项目文件中定义的或者在 MSBuild 提供的 .targets 文件中包括的经常使用的属性。  
  
 Visual Studio 中的项目文件（.csproj、.vbproj、vcxproj 等）包含你使用 IDE 生成项目时运行的 MSBuild XML 代码。 项目通常会导入一个或多个 .targets 文件以定义它们的生成过程。 有关详细信息，请参阅[.Targets 文件](../msbuild/msbuild-dot-targets-files.md)。  
  
## <a name="list-of-common-properties-and-parameters"></a>通用属性和参数的列表  
  
|属性或参数名|描述|  
|--------------------------------|-----------------|  
|AdditionalLibPaths|指定其他文件夹，编译器将在这些文件夹中查找引用程序集。|  
|AddModules|使编译器让指定文件中的所有类型信息可供正在编译的项目使用。 此属性等效于 `/addModules` 编译器开关。|  
|ALToolPath|可以找到 AL.exe 的路径。 此属性将重写 AL.exe 的当前版本，从而允许使用其他版本。|  
|ApplicationIcon|要传递给编译器以作为 Win32 图标嵌入的 .ico 图标文件。 该属性等效于 `/win32icon` 编译器开关。|  
|ApplicationManifest|指定用于生成外部用户帐户控制 (UAC) 清单信息的文件的路径。 它仅适用于面向 [!INCLUDE[windowsver](../includes/windowsver-md.md)] 的 Visual Studio 项目。<br /><br /> 在大多数情况，该清单是嵌入的。 但如果使用免注册的 COM 或 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署，则该清单可以是随应用程序程序集一起安装的外部文件。 有关更多信息，请参见本主题中的 NoWin32Manifest 属性。|  
|AssemblyOriginatorKeyFile|指定用于对程序集进行签名 ( .snk 或 .pfx) 并传递给 [ResolveKeySource 任务](../msbuild/resolvekeysource-task.md) 的文件，以便生成用于对程序集进行签名的实际密钥。|  
|AssemblySearchPaths|要在生成时引用程序集解析期间搜索的位置列表。 路径在此列表中的出现顺序是有含义的，因为先列出的路径优先于后列出的条目。|  
|AssemblyName|生成项目后的最终输出程序集的名称。|  
|BaseAddress|指定主输出程序集的基址。 此属性等效于 `/baseaddress` 编译器开关。|  
|BaseOutputPath|指定输出文件的基路径。 如果设置此属性，[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 将使用 `OutputPath = $(BaseOutputPath)\$(Configuration)\`。 示例语法：`<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>`|  
|BaseIntermediateOutputPath|在其中创建所有配置特定的中间输出文件夹的顶级文件夹。 默认值为 `obj\`。 下面的代码是一个示例：`<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>`|  
|BuildInParallel|一个布尔值，指示在使用多处理器 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 时并行生成还是清理项目引用。 默认值为 `true`，该值表示如果系统有多个核心或处理器，则将并行生成项目。|  
|BuildProjectReferences|一个布尔值，指示是否由 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 生成项目引用。 如果在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 集成开发环境 (IDE) 中生成项目，则设置为 `false`；否则设置为 `true`。|  
|CleanFile|将用作“清理缓存”的文件的名称。 清理缓存是要在清理操作期间删除的已生成文件的列表。 该文件由生成过程放在中间输出路径中。<br /><br /> 此属性只指定没有路径信息的文件名。|  
|CodePage|指定要用于编译中所有源代码文件的代码页。 此属性等效于 `/codepage` 编译器开关。|  
|CompilerResponseFile|可以传递给编译器任务的可选响应文件。|  
|Configuration|正在生成的配置，为“Debug”或“Release”。|  
|CscToolPath|[!INCLUDE[csprcs](../includes/csprcs-md.md)] 编译器 csc.exe 的路径。|  
|CustomBeforeMicrosoftCommonTargets|要在公用目标导入前自动导入的项目文件或目标文件的名称。|  
|DebugSymbols|一个布尔值，指示是否由生成来生成符号。<br /><br /> 在命令行上设置 **/p： DebugSymbols = false** 会禁用程序数据库 () 符号文件的生成。|  
|DefineConstants|定义条件编译器常数。 符号/值对是使用下面的语法指定的，并且彼此之间用分号分隔：<br /><br /> symbol1 = value1 ; symbol2 = value2<br /><br /> 该属性等效于 `/define` 编译器开关。|  
|DefineDebug|一个布尔值，指示是否定义 DEBUG 常量。|  
|DefineTrace|一个布尔值，指示是否定义 TRACE 常量。|  
|DebugType|定义要生成的调试信息的级别。 有效值为“full”、“pdbonly”和“none”。|  
|DelaySign|一个布尔值，指示是否对程序集进行延迟签名，而不对其进行完整签名。|  
|DisabledWarnings|禁止显示指定的警告。 只有警告标识符的数值部分是必须指定的。 多个警告之间用分号分隔。 此参数对应于 vbc.exe 编译器的 `/nowarn` 开关。|  
|DisableFastUpToDateCheck|一个只适用于 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的布尔值。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 生成管理器使用名为 FastUpToDateCheck 的进程来确定项目是否必须重新生成才能保持最新。 此进程比使用 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 来确定这一点更快。 通过将 DisableFastUpToDateCheck 属性设置为 `true`，可以跳过 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 生成管理器，并强制生成管理器使用 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 来确定项目是否为最新版本。|  
|DocumentationFile|作为 XML 文档文件生成的文件的名称。 此名称只包含文件名，不包含路径信息。|  
|ErrorReport|指定编译器任务报告内部编译器错误的方式。 有效值为“prompt”、“send”或“none”。 此属性等效于 `/errorreport` 编译器开关。|  
|ExcludeDeploymentUrl|如果项目文件包含下列任何元素， [GenerateDeploymentManifest 任务](../msbuild/generatedeploymentmanifest-task.md) 会将 deploymentProvider 标记添加到部署清单：<br /><br /> -   UpdateUrl<br />-   InstallUrl<br />-   PublishUrl<br /><br /> 不过，使用 ExcludeDeploymentUrl，可以防止 deploymentProvider 标记添加到部署清单，即使指定了任何上述 URL。 为此，请将以下属性添加到项目文件：<br /><br /> 注意：`<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` **** ExcludeDeploymentUrl 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 中未显示，并且仅可通过手动编辑项目文件进行设置。 设置此属性不影响在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中发布；即 deploymentProvider 标记仍将添加到 PublishUrl 指定的 URL。|  
|FileAlignment|指定输出文件各部分的对齐位置，以字节为单位。 有效值为 512、1024、2048、4096、8192。 此属性等效于 `/filealignment` 编译器开关。|  
|FrameworkPathOverride|指定 mscorlib.dll 和 microsoft.visualbasic.dll 的位置。 此参数等效于 vbc.exe 编译器的 `/sdkpath` 开关。|  
|GenerateDocumentation|一个布尔型参数，指示是否由生成来生成文档。 如果设置为 `true`，生成过程将生成文档信息，并将此信息与生成任务所创建的可执行文件或库的名称一同放置在 .xml 文件中。|  
|IntermediateOutputPath|如果未指定路径，则为从 `BaseIntermediateOutputPath` 派生的完整中间输出路径。 例如 \obj\debug\\。 如果此属性被重写，则设置 `BaseIntermediateOutputPath` 不起任何作用。|  
|KeyContainerName|强名称密钥容器的名称。|  
|KeyOriginatorFile|强名称密钥文件的名称。|  
|NoWin32Manifest|确定编译器是否在输出程序集中生成默认的 Win32 清单。 默认值 `false` 表示为所有应用程序生成默认的 Win32 清单。 此属性等效于 vbc.exe 的 `/nowin32manifest` 编译器开关。|  
|ModuleAssemblyName|要将编译好的模块并入其中的程序集的名称。 该属性等效于 `/moduleassemblyname` 编译器开关。|  
|NoLogo|一个指示是否关闭编译器徽标的布尔值。 此属性等效于 `/nologo` 编译器开关。|  
|NoStdLib|一个指示是否避免引用标准库 (mscorlib.dll) 的布尔值。 默认值为 `false`。|  
|NoVBRuntimeReference|一个布尔值，指示是否应将 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 运行时 (Microsoft.VisualBasic.dll) 包括为项目中的引用。|  
|NoWin32Manifest|一个布尔值，指示是否将用户帐户控制 (UAC) 清单信息嵌入在应用程序的可执行文件中。 它仅适用于面向 [!INCLUDE[windowsver](../includes/windowsver-md.md)] 的 Visual Studio 项目。 在使用 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 和免注册的 COM 部署的项目中，将忽略此元素。 `False`（默认值）指示是否将用户帐户控制 (UAC) 清单信息嵌入在应用程序的可执行文件中。 `True` 指定不嵌入 UAC 清单信息。<br /><br /> 此属性仅适用于针对 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的 [!INCLUDE[windowsver](../includes/windowsver-md.md)] 项目。 在使用 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 和免注册的 COM 部署的项目中，将忽略此属性。<br /><br /> 只有在不希望 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 在应用程序的可执行文件中嵌入任何清单信息时，才应该添加 NoWin32Manifest；此过程称为“虚拟化”**。 若要使用虚拟化，请按照下列方式设置 `<ApplicationManifest>` 和 `<NoWin32Manifest>`：<br /><br /> -   对于 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 项目，请删除 `<ApplicationManifest>` 节点。 （在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 项目中，如果存在 `<ApplicationManifest>` 节点，将忽略 `<NoWin32Manifest>`）。<br />-   对于 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 项目，请将 `<ApplicationManifest>` 设置为 `False`，并将 `<NoWin32Manifest>` 设置为 `True`。 （在 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 项目中，`<ApplicationManifest>` 会重写 `<NoWin32Manifest>`）。|  
|Optimize|一个布尔值，在设置为 `true` 时，允许进行编译器优化。 此属性等效于 `/optimize` 编译器开关。|  
|OptionCompare|指定如何进行字符串比较。 有效值为“binary”或“text”。 此属性等效于 vbc.exe 的 `/optioncompare` 编译器开关。|  
|OptionExplicit|一个布尔值，设置为 `true` 时，要求在源代码中显式声明变量。 此属性等效于 `/optionexplicit` 编译器开关。|  
|OptionInfer|一个布尔值，设置为 `true` 时，允许进行变量的类型推理。 此属性等效于 `/optioninfer` 编译器开关。|  
|OptionStrict|一个布尔值，设置为 `true` 时，将使得生成任务强制使用严格类型语义来限制隐式类型转换。 此属性等效于 vbc.exe 编译器的 `/optionstrict` 开关。|  
|OutputPath|相对于项目目录，例如“bin\Debug”，指定输出目录的路径。|  
|OutputType|指定输出文件的文件格式。 此参数可以具有下列值之一：<br /><br /> -   Library。 创建一个代码库。 （默认值）。<br />-   Exe。 创建控制台应用程序。<br />-   Module。 创建一个模块。<br />-   Winexe。 创建一个基于 Windows 的程序。<br /><br /> 此属性等效于 vbc.exe 编译器的 `/target` 开关。|  
|OverwriteReadOnlyFiles|一个布尔值，指示要让生成覆盖只读文件还是触发错误。|  
|PdbFile|正在发出的 .pdb 文件的文件名。 此属性等效于 csc.exe 编译器的 `/pdb` 开关。|  
|Platform|生成所面向的操作系统。 有效值是“Any CPU”、“x86”和“x64”。|  
|RemoveIntegerChecks|一个布尔值，指示是否禁用整数溢出错误检查。 默认值为 `false`。 此属性等效于 vbc.exe 编译器的 `/removeintchecks` 开关。|  
|SGenUseProxyTypes|一个布尔值，指示是否应由 SGen.exe 生成代理类型。<br /><br /> SGen 目标使用此属性来设置 UseProxyTypes 标志。 此属性默认为 true，并且没有更高属性的 UI。 若要生成非 webservice 类型的序列化程序集，请在导入 Microsoft.Common.Targets 或 C#/VB.targets 之前将此属性添加到项目文件并将其设为 false。|  
|SGenToolPath|一个可选的工具路径，指示在当前版本的 SGen.exe 被重写时可以获得 SGen.exe 的位置。|  
|StartupObject|指定包含 Main 方法或 Sub Main 过程的类或模块。 此属性等效于 `/main` 编译器开关。|  
|ProcessorArchitecture|解析程序集引用时使用的处理器架构。 有效值为“msil”、“x86”、“amd64”或“ia64”。|  
|RootNamespace|在命名嵌入资源时要使用的根命名空间。 此命名空间属于嵌入资源清单名称的一部分。|  
|Satellite_AlgorithmId|在创建附属程序集时要使用的 AL.exe 哈希算法的 ID。|  
|Satellite_BaseAddress|在使用 `CreateSatelliteAssemblies` 目标生成特定于区域性的附属程序集时要使用的基址。|  
|Satellite_CompanyName|要在附属程序集生成期间传入 AL.exe 的公司名称。|  
|Satellite_Configuration|要在附属程序集生成期间传入 AL.exe 的配置名称。|  
|Satellite_Description|要在附属程序集生成期间传入 AL.exe 的说明文本。|  
|Satellite_EvidenceFile|在具有资源名称“Security.Evidence”的附属程序集中嵌入指定文件。|  
|Satellite_FileVersion|为附属程序集中的“文件版本”字段指定字符串。|  
|Satellite_Flags|指定附属程序集中“标志”字段的值。|  
|Satellite_GenerateFullPaths|使生成任务对错误消息中报告的所有文件使用绝对路径。|  
|Satellite_LinkResource|将指定的资源文件链接至某个附属程序集。|  
|Satellite_MainEntryPoint|指定方法的完全限定名称（即 class.method），以用作在附属程序集生成期间将模块转换为可执行文件时的入口点。|  
|Satellite_ProductName|为附属程序集中的“产品”字段指定字符串。|  
|Satellite_ProductVersion|为附属程序集中的“ProductVersion”字段指定字符串。|  
|Satellite_TargetType|将附属程序集输出文件的文件格式指定为“library”、“exe”或“win”。 默认值为“library”。|  
|Satellite_Title|为附属程序集中的“标题”字段指定字符串。|  
|Satellite_Trademark|为附属程序集中的“商标”字段指定字符串。|  
|Satellite_Version|指定附属程序集的版本信息。|  
|Satellite_Win32Icon|在附属程序集中插入一个 .ico 图标文件。|  
|Satellite_Win32Resource|在附属程序集中插入一个 Win32 资源（.res 文件）。|  
|SubsystemVersion|指定生成的可执行文件可以使用的子系统的最低版本。 此属性等效于 `/subsystemversion` 编译器开关。 有关此属性的默认值的信息，请参阅 [/subsystemversion (Visual Basic) ](https://msdn.microsoft.com/library/08be22b2-f447-4cd3-8203-120b1b920b54) 或 [/Subsystemversion (c # 编译器选项) ](https://msdn.microsoft.com/library/a99fce81-9d92-4813-9874-bee777041445)。|  
|TargetCompactFramework|运行你所生成的应用程序所需要的 .NET Compact Framework 的版本。 通过指定此属性，你可以引用否则将无法引用的某些 Framework 程序集。|  
|TargetFrameworkVersion|运行生成的应用程序所需的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本。 通过指定此属性，你可以引用否则将无法引用的某些 Framework 程序集。|  
|TreatWarningsAsErrors|一个布尔型参数，如果设置为 `true`，则会导致将所有警告都视为错误。 此参数等效于 `/nowarn` 编译器开关。|  
|UseHostCompilerIfAvailable|一个布尔型参数，如果设置为 `true`，则会使得生成任务使用进程内编译器对象（如果可用）。 此参数只供 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 使用。|  
|Utf8Output|一个布尔型参数，如果设置为 `true`，则使用 UTF-8 编码记录编译器输出。 此参数等效于 `/utf8Output` 编译器开关。|  
|VbcToolPath|一个可选路径，在当前版本的 vbc.exe 被重写时它可以指示 vbc.exe 的另一个位置。|  
|VbcVerbosity|指定 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 编译器输出的详细级别。 有效值为“Quiet”、“Normal”（默认值）或“Verbose”。|  
|VisualStudioVersion|指定运行此项目应考虑使用的 Visual Studio 的版本。 如果未指定该属性，则 MSBuild 将其设置为合理的默认值。<br /><br /> 此属性在多种项目类型中用于指定要生成的目标组。 如果将某个项目的 `ToolsVersion` 设置为 4.0 或更高版本，则 `VisualStudioVersion` 将用于指定要使用的子工具集。 有关详细信息，请参阅[工具集 (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)。|  
|WarningsAsErrors|指定将被视为错误的警告的列表。 此参数等效于 `/warnaserror` 编译器开关。|  
|WarningsNotAsErrors|指定不被视为错误的警告的列表。 此参数等效于 `/warnaserror` 编译器开关。|  
|Win32Manifest|应嵌入最终程序集中的清单文件的名称。 此参数等效于 `/win32Manifest` 编译器开关。|  
|Win32Resource|要嵌入最终程序集中的 Win32 资源的文件名。 此参数等效于 `/win32resource` 编译器开关。|  
  
## <a name="see-also"></a>另请参阅  
 [常见的 MSBuild 项目项](../msbuild/common-msbuild-project-items.md)
