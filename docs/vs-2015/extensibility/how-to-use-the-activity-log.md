---
title: 如何：使用活动日志 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d450e02d23159f186fd85bf1b687a2fb2c18e82a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840712"
---
# <a name="how-to-use-the-activity-log"></a>如何：使用活动日志
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vspackage 可以将消息写入活动日志。 此功能对于在零售环境中调试 Vspackage 特别有用。  
  
> [!TIP]
> 始终打开活动日志。 Visual Studio 会保留最后100条目的滚动缓冲区以及前10个条目，其中包含常规配置信息。  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>将条目写入活动日志  
  
1. 将此代码插入 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法或除 VSPackage 构造函数之外的任何其他方法中：  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     此代码将获取 <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> 服务并将其强制转换为 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 接口。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> 使用当前的区域性上下文将信息性项写入活动日志。  
  
2. 加载 VSPackage 时 (通常在调用命令或打开窗口) 时，将文本写入活动日志。  
  
### <a name="to-examine-the-activity-log"></a>检查活动日志  
  
1. 找到 Visual Studio 数据的子文件夹中的活动日志： *% AppData%* \Microsoft\VisualStudio\14.0\ActivityLog.XML。  
  
2. 用任何文本编辑器打开活动日志。 下面是典型条目：  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>可靠编程  
 因为活动日志是一项服务，所以活动日志在 VSPackage 构造函数中不可用。  
  
 在写入活动日志之前，应立即获取该日志。 请勿缓存或保存活动日志以供将来使用。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Vspackage 故障排除](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
