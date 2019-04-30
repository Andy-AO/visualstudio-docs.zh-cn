---
title: 对项目和配置属性的支持 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a0858a3f1f1e98f7f6d0bde87036126ec31320f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428832"
---
# <a name="support-for-project-and-configuration-properties"></a>支持项目和配置属性
**属性**窗口中的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 可以显示的项目和配置属性。 可以项目类型提供属性页，以便用户可以设置为应用程序的属性。

 通过选择中的项目节点**解决方案资源管理器**，然后单击**属性**上**项目**菜单中，可以打开一个对话框，其中包括项目和配置属性。 在中[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]并[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]，和项目类型派生自这些语言，为选项卡式页面中会显示此对话框[General，Environment，Options Dialog Box](../../ide/reference/general-environment-options-dialog-box.md)。 有关详细信息，请参阅[不在生成中：演练：公开项目和配置属性 (C#)](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)。

 托管包框架中的项目 (MPFProj) 提供了用于创建和管理新的项目系统的帮助程序类。 可找到的源的代码和编译说明[项目的 Visual Studio 2013 的 MPF](https://github.com/tunnelvisionlabs/MPFProj10)。

## <a name="persistence-of-project-and-configuration-properties"></a>暂留的项目和配置属性
 项目和配置属性将保留在具有任何文件扩展名与项目类型，例如关联、.csproj、.vbproj 和.myproj 的项目文件。 语言项目通常使用的模板文件生成项目文件。 但是，有几种实际的方法以将项目类型和模板相关联。 有关详细信息，请参阅[模板目录说明 (。Vsdir) 文件](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)。

 通过将项添加到模板文件创建项目和配置属性。 然后，这些属性是可用于通过使用此模板的项目类型创建任何项目。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 项目和都使用的 MPFProj[不在生成中：MSBuild 概述](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90))模板文件的架构。 这些文件具有 PropertyGroup 部分为每个配置。 项目的属性通常将保留在配置参数设置为 null 字符串的第一个 PropertyGroup 部分。

 下面的代码演示了基本的 MSBuild 项目文件的开始。

```
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Name>SomeProjectSix</Name>
    <SchemaVersion>2.0</SchemaVersion>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
    <Optimize>false</Optimize>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <Optimize>true</Optimize>
```

 此项目文件中`<Name>`并`<SchemaVersion>`项目属性和`<Optimize>`是配置属性。

 它负责的项目，以保持项目文件的项目和配置属性。

> [!NOTE]
> 一个项目可以通过保留唯一属性值不同于其默认值的优化暂留。

## <a name="support-for-project-and-configuration-properties"></a>支持项目和配置属性
 `Microsoft.VisualStudio.Package.SettingsPage`类实现项目和配置属性页。 默认实现`SettingsPage`到泛型属性网格中的用户提供的公共属性。 `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids`方法选择类派生自`SettingsPage`的项目属性网格。 `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids`方法选择类派生自`SettingsPage`的配置属性网格。 您的项目类型应重写这些方法来选择相应的属性页。

 `SettingsPage`类和`Microsoft.VisualStudio.Package.ProjectNode`类提供这些方法以持久保存项目和配置属性：

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` 和`Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty`持久保存项目属性。

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` 和`Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty`保持配置属性。

  > [!NOTE]
  > 实现`Microsoft.VisualStudio.Package.SettingsPage`并`Microsoft.VisualStudio.Package.ProjectNode`类使用`Microsoft.Build.BuildEngine`(MSBuild) 方法来获取和设置从项目文件的项目和配置属性。

  从派生的类`SettingsPage`必须实现`Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges`和`Microsoft.VisualStudio.Package.SettingsPage.BindProperties`来持久保存项目文件的项目或配置属性。

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute 和注册表路径
 类派生自`SettingsPage`旨在在 Vspackage 中共享。 若要使 VSPackage 创建派生自的类`SettingsPage`，添加`Microsoft.VisualStudio.Shell.ProvideObjectAttribute`派生自的类到`Microsoft.VisualStudio.Shell.Package`。

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 该属性附加到 VSPackage 并不重要。 当 VSPackage 注册[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，可以创建任何对象的类 id (CLSID) 注册，以便调用<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A>可以创建它。

 可以创建的对象的注册表路径由组合<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>，word、 CLSID、 和对象类型的 guid。 如果`MyProjectPropertyPage`类具有一个 guid {3c693da2-5bca-49b3-bd95-ffe0a39dd723} 和 UserRegistryRoot 是 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp，则将 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio 注册表路径。\8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}。

## <a name="project-and-configuration-property-attributes-and-layout"></a>项目和配置属性的特性和布局
 <xref:System.ComponentModel.CategoryAttribute>， <xref:System.ComponentModel.DisplayNameAttribute>，和<xref:System.ComponentModel.DescriptionAttribute>特性确定布局、 设置标签和通用的属性页中的项目和配置属性的说明。 这些属性确定的类别，分别显示名称和选项的说明。

> [!NOTE]
> 等效的属性、 SRCategory、 LocDisplayName 和 SRDescription，使用字符串资源本地化和中定义[项目的 Visual Studio 2013 的 MPF](https://github.com/tunnelvisionlabs/MPFProj10)。

 考虑以下代码片断：

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 `MyConfigProp`配置属性将显示在配置属性页中作为**我的配置属性**类别中**My Category**。 如果选择了说明，**我说明**，将显示在说明面板中。

## <a name="see-also"></a>请参阅
- [添加和删除属性页](../../extensibility/adding-and-removing-property-pages.md)
- [项目](../../extensibility/internals/projects.md)
- [模板目录说明 (.Vsdir) 文件](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
