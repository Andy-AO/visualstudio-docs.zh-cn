---
title: 分析内存使用情况
ms.custom: seodec18
ms.date: 03/30/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f77fa9087673ff8e9a429caa27318a60f21d4a60
ms.sourcegitcommit: 14637be49401f56341c93043eab560a4ff6b57f6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075439"
---
# <a name="analyze-memory-usage"></a>分析内存使用情况

可以使用多种工具查找内存泄漏和低效内存使用情况，例如集成了调试程序的“内存使用情况”诊断工具，或性能探查器中的工具（如 .NET 对象分配工具和事后分析“内存使用情况”工具）。

通过内存使用率工具可以拍摄托管和本机内存堆的一个或多个快照  。 可收集 .NET、ASP.NET、本机或混合模式（.NET 和本机）应用的快照。 “内存使用情况”工具可以在打开的 Visual Studio 项目和已安装的 Microsoft Store 应用上运行，也可以附加到正在运行的应用或进程。 无论是否进行调试，都可以运行“内存使用情况”工具。 有关详细信息，请参阅[运行带或不带调试器的分析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。 在调试程序中，你可以打开和关闭内存分析，并查看按每个对象细分的内存使用情况。 可以在暂停执行时（例如在断点处）查看内存使用情况结果。

.NET 对象分配工具可帮助确定 .NET 代码中的分配模式和异常。 此工具仅作为事后分析工具运行。 可以在本地或远程计算机上运行此工具。

有关描述如何使用内存分析工具的详细说明，请参阅[分析内存使用情况](../profiling/memory-usage.md)教程和 [.NET 对象分配工具](../profiling/dotnet-alloc-tool.md)。

可 Windows 7 及更高版本中使用不带调试器的分析工具。 要运行带调试器的分析工具（“诊断工具”窗口），需具备 Windows 8 及更高版本。

## <a name="blogs-and-videos"></a>博客和视频

[调试时分析 CPU 和内存](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ 博客：Visual C++ 2015 中的内存分析](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>请参阅

- [分析不调试的内存使用情况](../profiling/memory-usage-without-debugging2.md)
- [使用 Visual Studio 分析](../profiling/index.yml)
- [首先了解分析工具](../profiling/profiling-feature-tour.md)
