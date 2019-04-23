---
title: 将命令添加到解决方案资源管理器中工具栏 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: 40
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 234f8ffbb3fdde48ca844386d5e5a716f74e8969
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054725"
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>将命令添加到解决方案资源管理器工具栏
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本演练演示如何将添加到按钮**解决方案资源管理器**工具栏。  
  
 在 Visual Studio 中，工具栏或菜单上的任何命令称为一个按钮。 当单击按钮时，将执行命令处理程序中的代码。 通常情况下，相关的命令组合在一起以形成一个组。 菜单或工具栏作为容器的组。 优先级确定菜单中或在工具栏上的组中的单个命令的显示的顺序。 您可以防止一个按钮工具栏或菜单上显示通过控制其可见性。 中列出的命令`<VisibilityConstraints>`.vsct 文件的部分仅在关联的上下文中出现。 可见性不能应用于组。  
  
 有关菜单、 工具栏命令和.vsct 文件的详细信息，请参阅[命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
> [!NOTE]
>  使用 XML 命令表格 (.vsct) 文件而不是命令表格 (.ctc) 配置文件来定义菜单和命令在你的 Vspackage 中的显示方式。 有关详细信息，请参阅 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## <a name="prerequisites"></a>系统必备  
 从 Visual Studio 2015 开始，您并不安装 Visual Studio SDK 从下载中心获得。 它是作为 Visual Studio 安装程序中的可选功能包含在内。 此外可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-an-extension-with-a-menu-command"></a>使用菜单命令创建扩展  
 创建一个名为的 VSIX 项目`SolutionToolbar`。 添加一个名为的菜单命令项模板**工具栏按钮**。 有关如何执行此操作的信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>将按钮添加到解决方案资源管理器工具栏  
 本演练的本部分演示如何将添加到按钮**解决方案资源管理器**工具栏。 单击按钮时，运行中的回调方法的代码。  
  
1. 在 ToolbarButtonPackage.vsct 文件中，转到`<Symbols>`部分。 `<GuidSymbol>`节点包含的菜单组和由包模板生成的命令。 添加`<IDSymbol>`到此节点，以声明将保存您的命令组的元素。  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2. 在`<Groups>`部分中，现有组项之后, 您声明的新组中定义在上一步。  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Guid: id 对的父级设置为`guidSHLMainMenu`并`IDM_VS_TOOL_PROJWIN`放入此组**解决方案资源管理器**工具栏中，并在设置高优先级值将其放在其他命令组的后面。  
  
3. 在中`<Buttons>`部分中，更改所生成的父 ID`<Button>`条目以反映您在上一步中定义的组。 已修改`<Button>`元素应如下所示：  
  
    ```xml  
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">  
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPicStrikethrough" />  
        <Strings>  
            <ButtonText>Invoke ToolbarButton</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
4. 生成项目并启动调试。 将显示在实验实例。  
  
     **解决方案资源管理器**工具栏应显示现有按钮右侧的新建命令按钮。 该按钮的图标带删除线。  
  
5. 单击新建按钮。  
  
     包含消息的对话框**ToolbarButtonPackage 内 SolutionToolbar.ToolbarButton.MenuItemCallback()** 应显示。  
  
## <a name="controlling-the-visibility-of-a-button"></a>控制按钮的可见性  
 本演练的本部分演示如何控制工具栏上的按钮的可见性。 通过将上下文设置为中的一个或多个项目`<VisibilityConstraints>`部分 SolutionToolbar.vsct 文件的限制的按钮才会显示仅当一个项目都打开。  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>当一个或多个项目打开时显示的按钮  
  
1. 在中`<Buttons>`部分的 ToolbarButtonPackage.vsct，将两个命令标志添加到现有`<Button>`元素之间`<Strings>`和`<Icons>`标记。  
  
   ```xml  
   <CommandFlag>DefaultInvisible</CommandFlag>  
   <CommandFlag>DynamicVisibility</CommandFlag>  
   ```  
  
    `DefaultInvisible`并`DynamicVisibility`标志必须设置操作中的该条目`<VisibilityConstraints>`部分才会生效。  
  
2. 创建`<VisibilityConstraints>`节，其中包含两个`<VisibilityItem>`条目。 恰好在关闭后将新的部分`</Commands>`标记。  
  
   ```xml  
   <VisibilityConstraints>  
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
             id="ToolbarButtonId"  
             context="UICONTEXT_SolutionHasSingleProject" />  
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
             id="ToolbarButtonId"  
             context="UICONTEXT_SolutionHasMultipleProjects" />  
   </VisibilityConstraints>  
   ```  
  
    可见性的每个项表示指定的按钮显示在其下的条件。 若要应用多个条件，必须创建多个条目为相同的按钮。  
  
3. 生成项目并启动调试。 将显示在实验实例。  
  
    **解决方案资源管理器**工具栏不包含删除线按钮。  
  
4. 打开包含项目的任何解决方案。  
  
    删除线按钮在现有按钮右侧的工具栏上显示。  
  
5. 上**文件**菜单上，单击**关闭解决方案**。 从工具栏中，按钮就会消失。  
  
   由控制按钮的可见性[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]直到加载 VSPackage。 VSPackage 加载后，由 VSPackage 控制按钮的可见性。  有关详细信息，请参阅[MenuCommands 与。OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)。  
  
## <a name="see-also"></a>请参阅  
 [命令、菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)
