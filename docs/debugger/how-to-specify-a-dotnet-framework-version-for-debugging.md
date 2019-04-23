---
title: 指定用于调试的.NET Framework 版本 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d2ce13fc55c94514bb9da24e43a5c54671becde5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080652"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging-c-visual-basic-f"></a>如何：指定用于调试的.NET Framework 版本 (C#，Visual Basic 中， F#)

Visual Studio 调试器支持调试较旧版本的 Microsoft[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]和当前版本。 如果从 Visual Studio 启动应用程序，则调试器可以始终为正在进行调试的应用程序识别 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的正确版本。 但是，如果应用程序已运行，而且您开始调试通过**将附加到**，调试器可能始终无法识别较旧版本的[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 如果发生这种情况，您将收到一条错误消息，指出：

``` cmd
The debugger has made an incorrect assumption about the [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] version your application is going to use.
```

在极少数的情况下，会出现此错误，可以设置注册表项以指示调试器要使用的版本。

### <a name="to-specify-a-net-framework-version-for-debugging"></a>指定用于调试的 .NET Framework 版本

1. 在 Windows\Microsoft.NET\Framework 目录中查找您计算机上安装的 .NET Framework 的版本。 这些版本号类似于：

    `V1.1.4322`

    识别正确的版本号并记录下来。

2. 启动“注册表编辑器”(regedit)。

3. 在“注册表编辑器”中打开 HKEY_LOCAL_MACHINE 文件夹。

4. 转到：HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}

    如果该密钥不存在，请右键单击 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine，然后单击“新建密钥”。 命名新的密钥`{449EC4CC-30D2-4032-9256-EE18EB41B62B}`。

5. 导航到 {449EC4CC-30D2-4032-9256-EE18EB41B62B} 后，在“名称”列中查找 CLRVersionForDebugging 密钥。

   1. 如果该密钥不存在，请右键单击 {449EC4CC-30D2-4032-9256-EE18EB41B62B}，然后单击“新建字符串值”。 然后右键单击新的字符串值，单击**重命名**，然后键入`CLRVersionForDebugging`。

6. 双击“CLRVersionForDebugging”。

7. 在“编辑字符串”框中，在“值”框中键入 .NET Framework 版本号。 例如：V1.1.4322

8. 单击 **“确定”**。

9. 关闭“注册表编辑器”。

     如果开始调试时仍然收到错误消息，请验证是否已在注册表中正确输入了版本号。 还请验证您是否正在使用 Visual Studio 支持的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。 调试器与 .NET Framework 当前版本及早期版本兼容，但可能与未来的版本不向前兼容。

## <a name="see-also"></a>请参阅
- [调试器设置和准备](../debugger/debugger-settings-and-preparation.md)