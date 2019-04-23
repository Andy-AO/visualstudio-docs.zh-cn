---
title: 如何：对服务进行故障排除 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 681564b2148fb9554e80105c2e18b1d220bb37ea
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111644"
---
# <a name="how-to-troubleshoot-services"></a>如何：排查服务问题
有几个常见的问题时尝试获得的服务可能发生的：

- 服务未注册与[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。

- 请求服务时通过接口类型而不是由服务类型。

- VSPackage 请求该服务没有就位。

- 使用错误的服务提供程序。

  如果所请求的服务无法获取，则会调用<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>，则返回 null。 您应始终测试存在 null 请求服务后：

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>若要对服务进行故障排除

1. 检查系统注册表，以查看是否已正确注册该服务。 有关详细信息，请参阅[如何：提供的服务](../extensibility/how-to-provide-a-service.md)。

    以下 *.reg*文件片断演示可能注册 SVsTextManager 服务的方式：

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    在上面的示例中，版本号是版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，如 12.0 或 14.0，{F5E7E71D-1401-11d1-883B-0000F87579D2} 的密钥是服务、 SVsTextManager 和默认值 {的服务标识符 (SID)F5E7E720-1401-11d1-883B-0000F87579D2} 是包的文本管理器提供服务的 VSPackage 的 GUID。

2. 在调用 GetService 时使用的服务类型而不是接口类型。 请求的一项服务时[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，<xref:Microsoft.VisualStudio.Shell.Package>从类型中提取 GUID。 如果满足下列条件，将不会找到一种服务：

   1. 接口类型而不是服务类型传递给 GetService。

   2. 没有 GUID 显式分配给的接口。 因此，系统会创建 GUID 的对象根据需要为默认值。

3. 请确保已就位 VSPackage 请求该服务。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 在构造它之后和调用之前站点 VSPackage <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>。

    如果 VSPackage 的构造函数中需要一种服务的代码，将其移动到`Initialize`方法。

4. 为确保使用正确的服务提供程序。

    并非所有服务提供程序都是等内容。 服务提供商的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]将传递到工具窗口不同于将其传递到 VSPackage。 工具窗口服务提供商知道<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>，但不知道有关<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>。 您可以调用<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>若要获取的 VSPackage 服务提供程序的工具窗口。

    如果工具窗口承载用户控件或任何其他控件容器，容器将通过 Windows 组件模型确定位置并不会访问任何[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]服务。 您可以调用<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>获取 VSPackage 服务提供商从控件容器中的。

## <a name="see-also"></a>请参阅
- [可用服务列表](../extensibility/internals/list-of-available-services.md)
- [使用和提供服务](../extensibility/using-and-providing-services.md)
- [服务基础知识](../extensibility/internals/service-essentials.md)