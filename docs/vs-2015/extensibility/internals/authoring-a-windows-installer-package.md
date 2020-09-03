---
title: 创作 Windows Installer 包 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58529dabbb52ceb751c67be24beb1d21285a1de6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "74301137"
---
# <a name="authoring-a-windows-installer-package"></a>创作 Windows Installer 程序包
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

数据驱动 Windows Installer 模型。 例如，您可以在数据库表中创作包含文件和注册表数据的行和列，而不是编写过程脚本来复制文件和写入注册表项。  
  
## <a name="database-entries"></a>数据库项  
 若要安装 VSPackage，Windows Installer 包必须包含用于执行以下任务的数据库条目：  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]使用包括 AppSearch、CompLocator、RegLocator、DrLocator 和签名) 的 Windows Installer 表，搜索系统以查找 VSPackage (支持的版本。  
  
- 如果未安装支持的版本 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，或者如果不 (满足 VSPackage 的其他系统要求，则取消安装，) 使用 LaunchCondition 表。  
  
- 使用) 的目录、组件和文件表 (安装 VSPackage 和相关文件。  
  
- 使用注册表)  (将 VSPackage 的相应信息添加到注册表中。  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]通过使用 CustomAction 表) 调用**devenv.exe/setup** (来集成中的 VSPackage。  
  
  有关详细信息，请参阅 [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)。  
  
## <a name="setup-tools"></a>安装工具  
 许多第三方安装工具为 Windows Installer 包提供了一个开发环境。 以下是两个免费工具：  
  
- InstallShield Limited Edition  
  
   可以通过 Visual Studio 的 " **新建项目** " 对话框获取有限版本的 InstallShield。 展开 " **其他项目类型** "，然后选择 " **安装和部署**"。 选择 InstallShield 模板。  
  
- Windows Installer XML 工具集  
  
   工具集生成 XML 源文件 Windows Installer 包。 工具集是一个 Microsoft 开源项目。 你可以从下载源代码和可执行文件 [http://sourceforge.net/projects/wix](https://sourceforge.net/projects/wix/) 。  
  
  有关使用集成到的商业产品 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] ，请参阅 [https://marketplace.visualstudio.com/](https://marketplace.visualstudio.com/) 。  
  
## <a name="see-also"></a>另请参阅  
 [使用 Windows Installer 安装 VSPackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
