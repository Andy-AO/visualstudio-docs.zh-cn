---
title: UML 组件图：准则 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99f2b67d264edcaab5272d0224d4450ee2e8a6f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297163"
---
# <a name="uml-component-diagrams-guidelines"></a>UML 组件图：准则
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中，你可以绘制 *组件图* 来显示软件系统的结构。 有关视频演示，请参阅 [使用组件图设计物理结构](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure)。

 若要查看支持此功能的 Visual Studio 的版本，请参阅 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

 若要创建 UML 组件图，请在 " **体系结构** " 菜单上单击 " **新建 UML 或层关系图**"。

 组件是可在其环境中替换的模块化单元。 它的内部是隐藏的，但它具有一个或多个定义完善的接口，通过该 *接口* 可以访问其功能。 组件还可以具有 *所需的接口*。 所需的接口定义该组件需要其他组件中的哪些功能或服务。 将多个组件的提供的接口和所需的接口相连接，可以构造更大的组件。 完整的软件系统可以理解为是一个组件。

 绘制组件图具有以下几个好处：

- 考虑与主要块有关的设计，可帮助开发团队理解现有设计并创建新设计。

- 认为系统是具有定义完善的提供接口和所需接口的组件集合，从而可以改进组件之间的分离。 这反过来又使设计更易于理解，且在需求发生更改时可以更容易地做出相应更改。

  无论设计已在使用或将要使用的语言或平台如何，您都可以使用组件图来表示您的设计。

## <a name="relationship-to-other-diagrams"></a><a name="OtherDiagrams"></a> 与其他关系图的关系
 您以将组件图与其他关系图结合使用。

|其他关系图|帮助您讨论和传达设计的这些方面|
|-------------------|--------------------------------------------------------------------|
|UML 序列图|-系统组件之间的交互<br />-组件内的部件之间的交互。<br /><br /> 有关详细信息，请参阅 [UML 序列图：准则](../modeling/uml-sequence-diagrams-guidelines.md)。|
|UML 类图|-组件的接口。 类图可让你详细了解接口的方法。<br />-跨组件接口在参数中发送的数据。<br /><br /> 有关详细信息，请参阅 [UML 类图：准则](../modeling/uml-class-diagrams-guidelines.md)。|
|活动图|-组件为响应传入消息而执行的内部处理。<br /><br /> 有关详细信息，请参阅 [UML 活动图：准则](../modeling/uml-activity-diagrams-guidelines.md)。|
|层关系图|-组件的逻辑体系结构层。<br /><br /> 有关详细信息，请参阅 [层关系图：参考](../modeling/layer-diagrams-reference.md)。|

## <a name="basic-steps-for-drawing-component-diagrams"></a><a name="Basics"></a> 绘制组件图的基本步骤
 有关组件图中的元素的参考信息，请参阅 [UML 组件图：参考](../modeling/uml-component-diagrams-reference.md)。

 有关如何在设计过程中使用组件图的详细信息，请参阅为 [应用程序的体系结构建模](../modeling/model-your-app-s-architecture.md)。

> [!NOTE]
> [编辑 UML 模型和关系图](../modeling/edit-uml-models-and-diagrams.md)中介绍了用于创建任何建模图的详细步骤。

#### <a name="to-create-a-component-diagram"></a>创建组件图

1. 在 " **体系结构** " 菜单上，单击 " **新建 UML 或层关系图**"。

2. 在 " **模板**" 下，单击 " **UML 组件图**"。

3. 命名该关系图。

4. 在 " **添加到建模项目**" 中，选择解决方案中的现有建模项目，或者 **创建一个新的建模项目**，然后单击 **"确定"**。

     此时将显示一个新的组件图，其中包含 UML **组件图** 工具箱。 该工具箱中包含所需的元素和关系。

### <a name="drawing-components"></a>绘制组件
 ![带有接口的组件](../modeling/media/uml-compdrawing.png "UML_CompDrawing")

 为系统或应用程序中的每个主要功能单元创建 *组件* (1) 。

 这方面的示例包括应用程序、硬件设备、Web 服务、.NET 程序集、程序类或一组类或者程序的任何可分段。

##### <a name="to-create-components"></a>创建组件

1. 单击工具箱中的 " **组件** "，然后单击关系图的空白部分。

     \- 或 -

     复制并粘贴现有组件。

    1. 在关系图或 **UML 模型资源管理器**中查找现有组件。

    2. 右键单击该组件，然后单击 " **复制**"。

    3. 打开希望在其中显示复制的组件的关系图。

    4. 右键单击关系图的空白部分，然后单击 " **粘贴**"。

         组件的副本随即以新名称显示。

2. 单击组件的名称以更改它。

3. 如果您只想看到组件的标头，请单击 V 形 (5)。

### <a name="showing-the-ports-of-a-component"></a>显示组件的端口
 *端口* (2，3) 表示一组传入或传出组件的消息或操作调用。 组由接口描述，而接口定义端口的类型。 端口可以提供接口也可以需要接口。

 具有 *提供的接口* (2) 提供由组件实现的、可供其他组件使用的端口。

 这方面的示例包括用户界面、Web 服务、.NET 接口或任何编程语言中的函数集合。

 具有 *所需接口* (3) 的端口表示组件对由其他组件或外部系统提供的一组操作或服务的要求。

 例如，Web 浏览器需要 Web 服务器，应用程序外接程序需要应用程序中的服务。

 组件可以具有任意数量的端口。

##### <a name="to-add-ports-to-a-component"></a>将端口添加到组件

1. 在工具箱中，单击 " **提供的接口** " 或 " **所需的接口**"。

2. 单击要将端口添加到的组件。

    端口随即显示在组件的边界上。

    新接口即作为端口的类型创建。 此接口显示在 " **UML 模型资源管理器**" 中。

3. 沿着组件边界拖动端口以将其放置在所需位置。

4. 拖动端口的标签以调整其位置。

5. 单击该标签以更改它。 标签显示接口的名称。 如果您更改了标签，则也更改了接口的名称。

   若要列出接口的特性和操作，可在 UML 模型资源管理器中将这些特性和操作添加到接口来做到这一点。 或者，可以将接口从 UML 模型资源管理器拖动到类图上，并在此位置添加操作和特性。

### <a name="linking-between-components"></a>在组件之间进行链接
 使用依赖项 (4) 以显示一个组件的要求可以通过其他组件提供的操作或服务来满足。

##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>显示提供的接口可以满足所需的接口

1. 在工具箱中，单击 " **依赖关系**"。

2. 单击一个组件上具有所需的接口的端口，再单击另一个组件上具有提供的接口的端口。

   应尝试避免设计依赖项循环，即组中的每个组件都依赖于所有其他组件。

##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>将现有接口的端口添加到组件

- 在 " **UML 模型资源管理器** " 中找到该接口，然后将其拖到组件上。

     - 或 -

- 复制引用并将其粘贴到关系图中的接口。

    1. 在类图或组件图上，右键单击接口，然后单击 " **复制**"。

    2. 在组件图上，右键单击该组件，然后单击 " **粘贴引用**"。

         提供的接口随即显示在组件上。 旁边显示了一个操作标记。

        > [!NOTE]
        > 如果使用 **paste** 而不是 **粘贴引用**，则将创建一个具有新名称的新接口。

    3. 如果要创建所需的接口，请单击操作标记，然后单击 " **转换为所需的接口**"。

## <a name="showing-the-internal-parts-of-a-component"></a><a name="Parts"></a> 显示组件的内部部件
 ![显示内部部件的组件图](../modeling/media/uml-compshowing.png "UML_CompShowing")

 可以将部件 (3) 放置在组件 (1) 中，以显示彼此进行交互的较小组件如何组成该组件。

 插图中的关系图指明，类型“立即就餐 Web 服务”的每个实例都包含一个“顾客服务器”实例和一个“厨房服务器”实例。

 部件是其父组件的属性，与属于普通类的特性非常类似。 部件有其自己的类型，该类型通常也是组件。 部件的标签与普通特性具有相同的形式：

 `+ partName : TypeName`

 在父组件内部，每个部件都显示了为其类型（4、5）定义的提供的接口和所需的接口。 一个部件需要的操作或服务可以由另一个部件提供。 您可以使用 **部件程序集** 连接器显示部件如何连接 (6) 。

 还可以显示父组件的某个部件实际提供还是需要该组件的接口。 您可以使用 **委托** 关系 (9) 将父级的端口连接到内部部件的端口。 这两个端口的类型必须相同（同时为提供或所需），且其接口类型应兼容。

 可以使用新类型或通过现有类型创建新部件。

#### <a name="to-add-parts-to-a-component"></a>将部件添加到组件

1. 为您认为是父组件的部件的每个主要功能单元创建一个部件。

    1. 单击工具箱中的 " **组件** "，然后在父组件)  (1 "中单击。

         新部件 (3) 随即显示在父组件中。

         在 **UML 模型资源管理器**中创建一个新的组件。 此组件是新部件的类型。

         \- 或 -

         将现有组件从 UML 模型资源管理器拖动到父组件。

         新部件 (3) 随即显示在父组件中。 其类型为从 UML 模型资源管理器拖动的组件。

         \- 或 -

         在关系图或 UML 模型资源管理器中右键单击组件，然后单击 " **复制**"。

         右键单击父组件，然后单击 " **粘贴引用**"。

         新部件 (3) 随即显示在父组件中。 其类型为所复制的组件。

    2. 单击新部件的名称以更改它。 您无法更改该部件的类型。

    3. 可以将提供的接口和所需的接口（4、5）添加到新部件。 单击 " **提供的接口** " 或 " **所需的接口** " 工具，然后单击部分。

         \- 或 -

         将现有接口从 " **UML 模型资源管理器** " 拖到该部件。

         接口随即添加到部件的类型，并显示在部件本身上。 父组件会根据需要调整接口的大小。

2. 将部件相互连接。

    - 使用 **依赖关系** 工具连接 (6) 不同部件的端口。

3. 将部件连接到父组件的端口：

    1. 在父组件上创建一个或多个端口 (7)。 单击工具箱上的 " **所需的接口** " 或 " **提供的接口** "，然后单击父组件。

    2. 将端口委托 (9) 给一个或多个部件。 单击 " **委派** " 工具，然后单击父组件上的端口，然后单击部件上的端口。 可以通过相同方式连接提供接口或需要接口的端口。

### <a name="showing-the-parts-of-a-part"></a>显示部件的多个部件
 将组件分解为多个部件后，可以将每个部件类型分解为其自己的内部部件。

 在单独的组件图中分解每个层最为简单。 首先必须找到部件的类型。 如插图所示，一个部件名为 `DNCustomerServer`，且其类型是称为 `CustomerServer` 的组件。 可以在 UML 模型资源管理器中找到该类型，并将其放置在其他关系图中。 然后，您可以创建该类型自己的内部部件。

##### <a name="to-place-a-parts-type-on-a-diagram"></a>将部件的类型放置到关系图上

1. 确定部件的类型的完全限定名。

     右键单击该部件，然后单击 " **属性**"。

     类型名称出现在属性窗口的 " **类型** " 字段中。

2. 在 **UML 模型资源管理器**中找到部件的类型。

     单击 " **查看**"，指向 " **其他窗口**"，再单击 " **UML 模型资源管理器**"。

     展开项目和该类型所属的任何包（如果需要）。

     该类型将作为 **组件**列出。

     如果需要，可以在此处更改类型的名称。

3. 打开或创建另一个组件图。

4. 从 UML 模型资源管理器中的类型拖动到该关系图上。

     类型的视图显示为关系图中的组件。

     该组件具有的接口与您为部件定义的接口相同。

     现在可以向组件中添加部件。

## <a name="designing-the-component"></a><a name="Designing"></a> 设计组件

### <a name="describing-how-the-parts-collaborate"></a>介绍部件的协作方式
 您可以绘制一个序列图，以显示各部件如何协同工作以响应到达父组件的消息。

 可以使用这些关系图来解释现有组件并设计新组件。

 如果您仍要设计组件，则可以先绘制一些序列图，然后再确定该组件将包含哪些部件。 可以使用这些序列图体验不同的部件、所需的接口和消息序列。 为最常用且最重要的传入消息绘制序列图。 然后可以在组件中创建与您已确定的生命线对应的部件。

 使用序列图可以判断系统的工作在不同组件之间是如何分布的。

- 如果一个部件上堆集了太多工作，则与在各个部件之间平均分布工作相比，应用程序可能更难更新。

- 如果工作在多个交互操作之间分布得非常稀疏，则系统在执行时可能会出错且可能会难以理解。

  ![显示协作部件的序列关系图](../modeling/media/uml-compdescparts.png "UML_CompDescParts")

##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>绘制显示各部件间的协作的序列图

1. 创建新的序列图。

     有关详细信息，请参阅 [UML 序列图：准则](../modeling/uml-sequence-diagrams-guidelines.md)。

2. 为向组件发送消息的外部组件、用户、设备或其他参与者 (1) 创建生命线。

     您可以将此生命线的执行 **组件属性设置** 为 true，以指示它在考虑的组件外部。 在生命线上方会出现一个简图。

3. 为所选参与者向其发送消息的组件的提供的接口 (2) 创建生命线。

4. 为组件的每个部件 (3) 创建生命线。

5. 为组件的每个所需的接口 (4) 创建生命线。

6. 基于外部参与者 (5) 绘制消息。 显示如何将消息传递给部件以及部件如何协同工作以响应消息。

7. 根据需要，显示发送到所需的接口 (6) 的消息。 不必显示执行消息时的任何详细信息。

### <a name="is-the-component-more-than-its-parts"></a>组件是否比其部件要多？
 在某些情况下，组件只是为部件集合指定的名称。 所有工作都由部件完成，在运行时，没有任何表示组件的代码或其他项目。

 您可以在模型中通过设置组件的 " **为间接实例化** " 属性来指示这一点。 在这种情况下，组件的所有接口都应位于端口上，且委托给内部部件。

### <a name="describing-the-process-inside-each-part"></a>介绍每个部件内的进程
 可以使用活动图显示组件处理每个传入消息的方式。 有关详细信息，请参阅 [UML 活动图：准则](../modeling/uml-activity-diagrams-guidelines.md)。

 ![带有数据缓冲区的活动图](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")

 使用“接受事件操作”(1) 显示传入消息启动新线程。

 使用对象节点和输入/输出指针显示信息流和信息的存储位置。 在示例中，对象节点 (2) 用于显示正在各个线程之间缓冲的项。

### <a name="defining-data-and-classes"></a>定义数据和类
 可以使用 UML 类图描述以下方面的详细内容：

- 组件的接口。 在将 requires 或 provides 端口添加到组件时，接口将显示在 UML 模型资源管理器中。 你可以将此接口拖动或复制到 UML 类图中，以显示其特性和操作以及与其他接口的关系。

- 在接口的操作参数中传递的数据。

- 组件中存储的数据，例如活动图的对象流中所示。

### <a name="general-dependencies-between-components"></a>组件之间的普通依赖项
 使用组件图只是显示设计的主要部件及其相互依赖项。

 ![组件之间的依赖项](../modeling/media/uml-compdepend.png "UML_CompDepend")

 使用 **依赖关系** 工具绘制依赖项。 这指示一个组件的设计依赖于另一个组件。

 依赖项具有以下典型类型：

- 一个组件调用另一个组件中的代码。

- 一个组件实例化在另一个类中定义的类。

- 一个组件使用另一个组件创建的信息。

  您可以使用依赖项箭头的名称来表示特定类型的使用情况。 若要设置名称，请右键单击箭头，然后单击 " **属性**"，然后在 "属性" 窗口中设置 " **名称** " 字段。

## <a name="see-also"></a>另请参阅
 [编辑 uml 模型和关系图](../modeling/edit-uml-models-and-diagrams.md) [uml 组件图：](../modeling/uml-component-diagrams-reference.md)引用 uml[序列图](../modeling/uml-sequence-diagrams-reference.md)：引用 Uml[用例图](../modeling/uml-use-case-diagrams-reference.md)：引用 uml[类图](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) ：引用[视频：引用视频：使用组件图设计物理结构](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure)
