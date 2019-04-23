---
title: 组件管理 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 56a110f382d0b182eed0ea1a95cd4dabf2877037
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60090441"
---
# <a name="component-management"></a>组件管理
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Windows 安装程序中的任务的单位称为 （有时称为 WICs 或只是组件） 的 Windows 安装程序组件。 一个 GUID 标识每个 WIC，它是安装和引用计数对于使用 Windows 安装程序安装的基本单位。  
  
 虽然可以使用多个产品创建 VSPackage 安装程序，这一讨论都假定使用 Windows Installer (.msi) 文件。 在创建您的安装程序时，必须正确地管理文件部署，以便正确引用计数在任何时候进行。 因此，您产品的不同版本将不会干扰或中断彼此中混合使用安装和卸载方案。  
  
 在 Windows 安装程序中，引用计数在组件级别进行。 必须小心地组织资源-文件、 注册表项等 — 为组件。 有其他级别的组织，如模块、 功能和产品 — 在不同情况下，可以帮助。 有关详细信息，请参阅[Windows Installer 基本知识](../../extensibility/internals/windows-installer-basics.md)。  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>创作的并行安装的安装程序的指导原则  
  
- 作者文件和注册表项在版本间共享到他们自己的组件。  
  
     这允许您轻松地在下一版本中使用它们。 例如，全局，注册类型库的文件扩展名，其他项注册 HKEY_CLASSES_ROOT，依此类推。  
  
- 分组到单独的合并模块中的共享的组件。  
  
     这可以帮助您编写正确地为通过并行下一步。  
  
- 跨版本使用相同的 Windows Installer 组件安装共享的文件和注册表项。  
  
     如果使用不同的组件，则会卸载文件和注册表项时卸载一个版本控制的 VSPackage，但仍安装另一个 VSPackage。  
  
- 不要混合在同一组件中的进行版本控制和共享项。  
  
     执行此操作会导致无法安装到全局位置和版本控制隔离的位置的项的共享的项。  
  
- 没有共享的注册表项指向版本控制文件。  
  
     如果这样做，安装另一个版本控制的 VSPackage 时，将被覆盖的共享的密钥。 删除第二个版本后，该密钥指向该文件是消失了。  
  
## <a name="see-also"></a>请参阅  
 [共享和版本控制的 Vspackage 之间进行选择](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage 安装方案](../../extensibility/internals/vspackage-setup-scenarios.md)
