---
title: 如何：启用和禁用编辑并继续 |Microsoft Docs
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
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d564162a92976037729c4ad638136d7c1e827c4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438292"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>如何：启用和禁用编辑并继续
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以禁用或启用在编辑并继续**选项**在设计时对话框。 无法在调试过程中更改此设置。  
  
 “编辑并继续”仅在调试版本中起作用。 对于本机 C++，“编辑并继续”需要使用 /INCREMENTAL 选项。  
  
## <a name="procedures"></a>过程  
  
#### <a name="to-enabledisable-edit-and-continue"></a>启用/禁用“编辑并继续”  
  
1. 打开调试选项页 (**工具 / 选项 / 调试**)。  
  
2. 向下滚动到**编辑并继续**类别。  
  
3. 若要启用，请选择**启用编辑并继续**复选框。 若要禁用它，请清除该复选框。  
  
   > [!NOTE]
   > 如果启用了 IntelliTrace 并且收集 IntelliTrace 事件和调用信息，则会禁用“编辑并继续”。 有关详细信息，请参阅[配置 IntelliTrace](http://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)。  
  
4. 单击 **“确定”**。  
  
   有关这些选项的详细信息，请参阅[General，Debugging，Options Dialog Box](../debugger/general-debugging-options-dialog-box.md)。  
  
## <a name="see-also"></a>请参阅  
 [编辑并继续](../debugger/edit-and-continue.md)
