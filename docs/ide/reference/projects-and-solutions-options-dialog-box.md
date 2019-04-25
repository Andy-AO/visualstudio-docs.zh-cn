---
title: “选项”对话框 ->“项目和解决方案”
ms.date: 07/14/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21d101ff4cd8503935fceb72b5350a6ce0e1ce2e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969067"
---
# <a name="projects-and-solutions-page-options-dialog-box"></a>“选项”对话框 ->“项目和解决方案”页

设置与项目和解决方案相关的 Visual Studio 行为。 要访问这些选项，请选择“工具” > “选项”，展开“项目和解决方案”，再选择“常规”。

通过相同对话框中的“位置”选项卡设置项目和模板文件夹的默认路径。

## <a name="general-page"></a>常规页

“常规”页上提供了下列选项。

### <a name="always-show-error-list-if-build-finishes-with-errors"></a>如果生成完成时有错误，则始终显示错误列表

仅当项目无法生成时，在完成生成时将打开“错误列表”窗口。 将显示在生成过程中发生的错误。 如果清除此选项，则仍将发生错误，但在完成生成时窗口将不会打开。 默认情况下会启用此选项。

### <a name="track-active-item-in-solution-explorer"></a>跟踪解决方案资源管理器中的活动项

当选中时，“解决方案资源管理器”将自动打开，活动项处于选中状态。 选定的项根据您在项目或解决方案中使用的不同文件或设计器中的不同组件而不同。 清除此选项后，“解决方案资源管理器”中的所选内容不会自动更改。 默认情况下会启用此选项。

### <a name="show-advanced-build-configurations"></a>显示高级生成配置

当选中时，生成配置选项显示在“项目属性页”对话框和“解决方案属性页”对话框中。 如果未选中，对于包含一个配置或两个配置调试和发布的 Visual Basic 和 C# 项目，生成配置选项将不显示在“项目属性页”对话框和“解决方案属性页”对话框中。 如果一个项目具有用户定义的配置，则会显示生成的配置选项。

未选中时，“生成”菜单上的命令（如“生成解决方案”、“重新生成解决方案”和“清理解决方案”）将在发布配置上执行，“调试”菜单上的命令（如“启动调试”和“启动但不调试”）将在调试配置上执行。

### <a name="always-show-solution"></a>总是显示解决方案

如果选中，该解决方案和解决方案中执行的所有命令将始终显示在 IDE 中。 未选中时，如果该解决方案只包含一个项目，所有项目将作为独立项目创建，您不会看到在解决方案资源管理器中的解决方案或 IDE 中解决方案的执行命令。

::: moniker range="vs-2017"

### <a name="save-new-projects-when-created"></a>创建时保存新项目

当选中时，你可以在“新建项目”对话框中为你的项目指定位置。 如果未选中，所有新项目将创建为临时项目。 当您正在使用临时项目时，您可以创建和试验项目，无需指定磁盘位置。

::: moniker-end

### <a name="warn-user-when-the-project-location-is-not-trusted"></a>当项目位置不受信任时警告用户

如果您尝试在不完全信任的位置（例如，在 UNC 路径或 HTTP 路径）创建一个新项目或打开现有项目，将显示一条消息。 使用此选项以指定每次在不完全受信任的位置尝试创建或打开一个项目时是否显示该消息。

### <a name="show-output-window-when-build-starts"></a>在生成开始时显示输出窗口

在解决方案生成一开始就在 IDE 中自动显示[输出窗口](../../ide/reference/output-window.md)。

### <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>在重命名文件时提示重命名符号

选定后，Visual Studio 将显示一个消息框，询问是否还应该将项目中的所有引用重命名为代码元素。

### <a name="prompt-before-moving-files-to-a-new-location"></a>将文件移动到新位置之前显示提示

选定后，在通过解决方案资源管理器中的操作更改文件的位置之前，Visual Studio 会显示确认消息框。

### <a name="reopen-documents-on-solution-load"></a>加载解决方案时重新打开文档

**在 Visual Studio 2017 版本 15.8 中引入**

选中后，此解决方案上次关闭时打开的文档将在解决方案打开时自动打开。

重新打开某些类型的文件或设计器会延迟解决方案加载。 如果不想还原解决方案的上一个上下文，请取消选中此选项以[提高解决方案加载性能](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore)。

## <a name="locations-page"></a>位置页

“位置”页上提供了下列选项。

### <a name="projects-location"></a>项目位置

指定 Visual Studio 在其中创建新的项目和解决方案文件夹的默认位置。 几个对话框还使用此选项中为文件夹起始点设置的位置。 例如，“打开项目”对话框将此位置用于“我的项目”的快捷方式。

### <a name="user-project-templates-location"></a>用户项目模板位置

指定用于搜索用户创建的项目模板的默认位置。 有关详细信息，请参阅[如何：查找和组织模板](../../ide/how-to-locate-and-organize-project-and-item-templates.md)。

### <a name="user-item-templates-location"></a>用户项模板位置

指定用于搜索用户创建的项模板的默认位置。 有关详细信息，请参阅[如何：查找和组织模板](../../ide/how-to-locate-and-organize-project-and-item-templates.md)。

## <a name="see-also"></a>请参阅

- [“选项”对话框 ->“项目和解决方案”->“生成和运行”](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [“选项”对话框 ->“项目和解决方案”->“Web 项目”](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
