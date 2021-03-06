---
title: 适用于 Android 的 Visual Studio 仿真程序 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
caps.latest.revision: 7
ms.author: crdun
manager: crdun
ms.openlocfilehash: af3dd595b786c57983e44982fa2eb8b9afa2959a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300772"
---
# <a name="visual-studio-emulator-for-android"></a>适用于 Android 的 Visual Studio 仿真程序
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

适用于 Android 的 Visual Studio 仿真器是一款可模拟 Android 设备的桌面应用程序。 它提供虚拟化的环境，你不需要物理设备便可在其中调试并测试 Android 应用程序。 它还为应用程序原型提供一个独立的环境。  
  
 适用于 Android 的 Visual Studio 仿真程序旨在为实际设备提供水平相当的性能。 但是，在发布你的应用之前，我们建议你在物理设备上测试应用。  
  
 你可以为每个 Android 平台、屏幕分辨率和适用于 Android 的 Visual Studio 仿真程序支持的其他硬件属性，在唯一设备配置文件上测试应用。  
  
 本主题包含以下各节：  
  
- [安装和卸载](#Installing)  
  
- [系统要求和向后兼容性](#Requirements)  
  
- [适用于 Android 的 Visual Studio 仿真程序中的网络](#Networking)  
  
- [配置适用于 Android 的 Visual Studio 仿真程序](#Configuring)  
  
- [可在模拟器中测试的功能](#FeaturesTest)  
  
- [无法在仿真程序中测试的功能](#FeaturesNonTest)  
  
- [支持资源](#Support)  
  
## <a name="installing-and-uninstalling"></a><a name="Installing"></a> 安装和卸载  
 安装  
  
 适用于 Android 的 Visual Studio 仿真程序是 Visual Studio 中提供的跨平台工具的一个组件，并可在你选择跨平台移动开发，然后选择常用工具和软件开发工具包，然后选择适用于 Android 的 Visual Studio 仿真程序时，在安装自定义 Visual Studio 期间安装。  
  
 卸载  
  
 你可以使用控制面板中的“添加/删除程序”功能卸载 Android 的 Visual Studio 仿真程序。  
  
> [!NOTE]
> 卸载 Visual Studio 将不会卸载该仿真程序。 你必须单独卸载该仿真程序。  
  
 在卸载适用于 Android 的 Visual Studio 仿真程序时，不会自动删除为仿真程序创建的 Hyper-V 虚拟以太网适配器。 通过打开 Hyper-V 管理器，选中其中一个仿真程序 VHD 映像，选择“网络”选项卡并为显示在此选项卡中的每个开关选择“删除”****，可以手动删除这些虚拟适配器（如果未使用）。  
  
## <a name="system-requirements-and-backward-compatibility"></a><a name="Requirements"></a> 系统需求和向后兼容性  
 有关硬件、软件和适用于 Android Visual Studio 仿真程序的配置需求的重要信息，请参阅以下主题。  
  
- [适用于 Android 的 Visual Studio 仿真程序的系统要求](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
  适用于 Android 的 Visual Studio 仿真程序需要 Visual Studio 2015；它不与 Visual Studio 的早期版本向后兼容。  
  
  新版本的仿真程序在旧版本的基础上安装（可能在某些情况下，替换旧的映像，放弃设置、应用和这些映像上安装的文件）。  
  
## <a name="networking-in-the-visual-studio-emulator-for-android"></a><a name="Networking"></a> 适用于 Android 的 Visual Studio 仿真程序中的网络  
 适用于 Android 的 Visual Studio 仿真程序的网络连接类似于具有以下特征的台式计算机的连接：  
  
- 该仿真程序可作为具有自己 IP 地址的单独设备出现在网络上。  
  
- 它不需要任何其他尚未使用仿真程序安装的网络软件。  
  
- 不可以加入 Windows 域。  
  
  若要了解仿真程序的网络连接的功能，将其视为类似于从 Android 手机到同一个网络的 Wi-Fi 连接。 如果手机上运行的应用可以通过其 Wi-Fi 连接访问网络资源，那么仿真程序上运行的应用程序还可以访问同一网络资源。  
  
  有关网络要求的详细信息，请参阅[适用于 Android 的 Visual Studio 仿真程序的系统需求](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
  有关对网络问题进行疑难解答的信息，请参阅[适用于 Android 的 Visual Studio 仿真程序的疑难解答](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)。  
  
## <a name="configure-the-visual-studio-emulator-for-android"></a><a name="Configuring"></a> 配置适用于 Android 的 Visual Studio 仿真程序  
 测试 Android 应用在多种 Android 硬件间的兼容性可能是一个挑战。 市场中的 Android 手机和平板电脑的版本和屏幕大小种类繁多，都具有许多不同的硬件配置（RAM、CPU、体系结构等）。 适用于 Android 的 Visual Studio 仿真程序通过使用设备配置文件对其进行了简化。 我们的设备配置文件集代表市场内最流行的硬件，包括Samsung、Motorola、Sony、LG 等的设备。  
  
 在 Visual Studio 2015 中，可以通过使用仿真程序管理器安装、卸载和启用设备配置文件。 通过选择“工具”****，然后选择“适用于 Android 的 Visual Studio 仿真程序”**** 访问仿真程序管理器。  
  
 ![适用于 Android 管理器的 Visual Studio 仿真程序](../cross-platform/media/android-emu-manager.png "Android_Emu_Manager")  
  
 默认情况下，有四个预安装的设备配置文件（KitKat 和 Lollipop 手机/5"和平板电脑/7"配置），如下白色文本和图标所示。 在选择“安装配置文件”**** 按钮以及安装完成之前，列表中的其他配置文件将显示处于灰显状态。 可以按 API 级别筛选列表，然后单击配置文件底部右侧上的详细信息箭头，查看其完整的配置详细信息。  
  
 安装想要设为目标的配置文件集后，可按绿色“播放”**** 按钮直接从管理器启用这些新的配置文件。 它们还将在任何 Visual Studio 跨平台移动项目类型中的调试目标下拉列表菜单中显示。  
  
## <a name="features-that-you-can-test-in-the-emulator"></a><a name="FeaturesTest"></a> 可在仿真程序中测试的功能  
 有关可在仿真程序中测试的功能的详细信息，请参阅此[文档](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/)。  
  
## <a name="features-that-you-cant-test-in-the-emulator"></a><a name="FeaturesNonTest"></a> 无法在仿真程序中测试的功能  
 下表描述无法在仿真程序中测试的 Android 平台的功能****。 必须在物理设备上测试这些功能。  
  
- 指南针  
  
- 陀螺仪  
  
- 振动控制器  
  
- 亮度。 更改仿真程序的亮度级别不会在视觉上影响设备在屏幕上的显示方式。  
  
## <a name="support-resources"></a><a name="Support"></a> 支持资源  
 如果你的主机计算机满足系统要求，但你遇到本疑难解答指南中未涉及的问题：  
  
- 使用 [Android 仿真程序](https://stackoverflow.com/questions/tagged/android-emulator) 和 Visual Studio 标记询问有关 StackOverflow 的问题。  
  
- 在 Visual Studio 或在仿真程序管理器中使用“发送笑脸”工具来报告问题。  
  
## <a name="see-also"></a>另请参阅  
 [适用于 Android 的 Visual Studio 仿真程序的系统要求](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)   
 [Troubleshooting the Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
