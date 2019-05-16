---
title: 演练：编写可视化工具C#|Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 190ada55d5f46d159c6765e9af83d672b654313d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688159"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>演练：在 C 中编写可视化工具\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本演练演示如何使用 C# 编写简单的可视化工具。 本演练中创建的可视化工具使用 Windows 窗体消息框显示字符串的内容。 此简单字符串可视化工具不是特别有用，但它显示创建更有用的其他数据类型的可视化工具时必须遵循的基本步骤。

> [!NOTE]
> 显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你的当前设置或版本。 若要更改设置，请转到**工具**菜单，然后选择**导入和导出设置**。 有关详细信息，请参阅 [在 Visual Studio 中自定义开发设置](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

可视化工具代码必须位于一个 DLL，将由调试器读取。 因此，第一步是为 DLL 创建一个类库项目。

#### <a name="to-create-a-class-library-project"></a>创建类库项目

1. 上**文件**菜单中，选择**新建**，然后单击**新项目**。

2. 在中**新的项目**对话框中的**项目类型**s，选择**Visual C#**。

3. 在中**模板**框中，选择**类库**。

4. 在“名称”框中，为类库键入一个适当的名称，例如 MyFirstVisualizer。

5. 单击 **“确定”**。

   创建类库后，必须添加对 Microsoft.VisualStudio.DebuggerVisualizers.DLL 的引用，以便使用其中定义的类。 添加引用之前，但是，您必须重命名的一些类，使其具有有意义的名称。

#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>若要将 Class1.cs 重命名并添加 Microsoft.VisualStudio.DebuggerVisualizers

1. 在中**解决方案资源管理器**，右键单击 Class1.cs，然后选择**重命名**快捷菜单上。

2. Class1.cs 的名称更改为有意义的名称，例如 debuggerside.cs。

   > [!NOTE]
   > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 自动更改在 debuggerside.cs 中以便与新文件名匹配的类声明。

3. 在中**解决方案资源管理器**，右键单击**引用**，然后选择**添加引用**快捷菜单上。

4. 在中**添加引用**对话框中，在 **.NET**选项卡上，选择 Microsoft.VisualStudio.DebuggerVisualizers.DLL。

5. 单击 **“确定”**。

6. 在 DebuggerSide.cs 中，将下面的语句添加到 `using` 语句中：

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   现在已经准备好创建调试器端代码了。 这是运行在调试器中以显示要可视化的信息的代码。 首先，您必须更改的声明`DebuggerSide`对象，以便从基类继承的`DialogDebuggerVisualizer`。

#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>从 DialogDebuggerVisualizer 继承

1. 在 debuggerside.cs 中，转到以下代码行：

   ```csharp
   public class DebuggerSide
   ```

2. 将代码更改为：

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` 具有一个抽象方法 (`Show`)，必须重写此方法。

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>重写 DialogDebuggerVisualizer.Show 方法

- 在 `public class DebuggerSide` 中添加下面的方法：

  ```csharp
  override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  `Show` 方法包含实际创建可视化工具对话框或其他用户界面的代码，并显示已从调试器传递到可视化工具的信息。 您必须添加创建该对话框并显示该信息的代码。 在本演练中，将使用 Windows 窗体消息框执行此操作。 首先，必须添加的引用和`using`System.Windows.Forms 的语句。

#### <a name="to-add-systemwindowsforms"></a>添加 System.Windows.Forms

1. 在中**解决方案资源管理器**，右键单击**引用**，然后选择**添加引用**快捷菜单上。

2. 在中**添加引用**对话框中，在 **.NET**选项卡上，选择 system.windows.forms.dll 的引用。

3. 单击 **“确定”**。

4. 在 DebuggerSide.cs 中，将下面的语句添加到 `using` 语句中：

   ```csharp
   using System.Windows.Forms;
   ```

   现在，可添加一些代码以创建和显示可视化工具的用户界面。 由于这是你第一个可视化工具，我们将简化用户界面，并使用一个消息框。

#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>在对话框中显示可视化工具输出

1. 在 `Show` 方法中，添加以下代码行：

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    此代码示例中不包含错误处理。 但在实际的可视化工具或任何其他类型的应用程序中，应当包含错误处理。

2. 上**构建**菜单中，选择**生成 MyFirstVisualizer**。 该项目应能成功生成。 在继续前更正所有生成错误。

   这是调试器端代码的结尾部分。 但是还有一步操作：添加用于通知调试对象端哪些类集合构成可视化工具的属性。

#### <a name="to-add-the-debuggee-side-code"></a>若要添加的调试对象端代码

1. 后向 debuggerside.cs 中，添加以下特性代码`using`语句之前`namespace MyFirstVisualizer`:

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target  = typeof(System.String),
   Description  = "My First Visualizer")]
   ```

2. 上**构建**菜单中，选择**生成 MyFirstVisualizer**。 该项目应能成功生成。 在继续前更正所有生成错误。

   这时，第一个可视化工具就完成了。 如果您已正确地按照每一步操作，您可以生成该可视化工具，并将其安装到 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中。 但在将可视化工具安装到 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中之前，应对其进行测试以确保它能够正常运行。 你现在将创建一个测试套以在没有将可视化工具安装到 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中的情况下运行它。

#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>添加测试方法以显示可视化工具

1. 将下面的方法添加到类 `public DebuggerSide`：

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. 上**构建**菜单中，选择**生成 MyFirstVisualizer**。 该项目应能成功生成。 在继续前更正所有生成错误。

   然后，您必须创建一个可执行项目以调用可视化工具 DLL。 为简单起见，我们将使用一个控制台应用程序项目。

#### <a name="to-add-a-console-application-project-to-the-solution"></a>将控制台应用程序项目添加到解决方案中

1. 上**文件**菜单中，选择**添加**，然后单击**新项目**。

2. 在中**添加新项目**对话框中**模板**框中，选择**控制台应用程序**。

3. 在中**名称**框中，键入有意义的名称的控制台应用程序，例如`MyTestConsole`。

4. 单击 **“确定”**。

   现在，必须添加必要的引用，以便 MyTestConsole 能够调用 MyFirstVisualizer。

#### <a name="to-add-necessary-references-to-mytestconsole"></a>添加对 MyTestConsole 的必需引用

1. 在中**解决方案资源管理器**，右键单击**MyTestConsole** ，然后选择**添加引用**快捷菜单上。

2. 在中**添加引用**对话框中， **.NET**选项卡上，选择 Microsoft.VisualStudio.DebuggerVisualizers.DLL。

3. 单击 **“确定”**。

4. 右键单击**MyTestConsole** ，然后选择**添加引用**试。

5. 在中**添加引用**对话框中，单击**项目**选项卡，然后单击 MyFirstVisualizer。

6. 单击 **“确定”**。

   现在，你将添加代码以完成测试套。

#### <a name="to-add-code-to-mytestconsole"></a>将代码添加到 MyTestConsole

1. 在中**解决方案资源管理器**，右键单击 Program.cs，然后选择**重命名**快捷菜单上。

2. 编辑而言更有意义，例如 TestConsole.cs 中 Program.cs 的名称。

    **请注意** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] TestConsole.cs 以匹配新的文件名称中的类声明将自动更改。

3. 在 TestConsole.cs，将以下代码添加到`using`语句：

   ```csharp
   using MyFirstVisualizer;
   ```

4. 在方法 `Main` 中，添加以下代码：

   ```
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   现在已准备好测试你的第一个可视化工具了。

#### <a name="to-test-the-visualizer"></a>测试可视化工具

1. 在中**解决方案资源管理器**，右键单击**MyTestConsole** ，然后选择**设为启动项目**快捷菜单上。

2. 在“调试”菜单上选择“启动”。

    控制台应用程序启动和可视化工具显示并显示字符串"Hello，World"。

   祝贺您！ 你刚刚生成了第一个可视化工具并进行了测试。

   如果您想在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中使用可视化工具，而不是只从测试工具中调用它，则需要安装它。 有关详细信息，请参阅[如何：安装可视化工具](../debugger/how-to-install-a-visualizer.md)。

## <a name="using-the-visualizer-item-template"></a>使用可视化工具项模板
 到目前为止，本演练说明了如何手动创建可视化工具。 作为练习执行此操作。 现在，您知道简单的可视化工具的工作原理，轻松地创建一个，则是： 使用可视化工具项模板。

 首先，您必须创建一个新的类库项目。

#### <a name="to-create-a-new-class-library"></a>若要创建新的类库

1. 上**文件**菜单中，选择**添加**，然后单击**新项目**。

2. 在中**添加新项目**对话框中的**项目类型**s，选择**Visual C#**。

3. 在中**模板**框中，选择**类库**。

4. 在中**名称**框中，键入为类库，如 MySecondVisualizer 的合适名称。

5. 单击 **“确定”**。

   现在，可以将可视化工具项添加到它：

#### <a name="to-add-a-visualizer-item"></a>若要添加的可视化工具项

1. 在中**解决方案资源管理器**，右键单击 MySecondVisualizer。

2. 在快捷菜单上，选择**外**，然后单击**新项**。

3. 在中**添加新项**对话框中的**模板**， **Visual Studio 已安装的模板**，选择**调试器可视化工具**。

4. 在中**名称**框中，键入相应的名称，例如 SecondVisualizer.cs。

5. 单击 **添加**。

   这是就是它。 看一下 SecondVisualizer.cs 的文件并查看该模板为您添加的代码。 请继续并代码。 现在，你了解基本知识，您可以为您创建更复杂且有用的可视化工具自己。

## <a name="see-also"></a>请参阅

- [可视化工具体系结构](../debugger/visualizer-architecture.md)
- [如何：安装可视化工具](../debugger/how-to-install-a-visualizer.md)
- [创建自定义可视化工具](../debugger/create-custom-visualizers-of-data.md)
