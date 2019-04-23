---
title: 模板目录说明 (。Vsdir) 文件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89152fcb003886087704107f2d4c2a66d3313cc3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050357"
---
# <a name="template-directory-description-vsdir-files"></a>模板目录说明 (.Vsdir) 文件
模板目录说明文件 (.vsdir) 是使集成的开发环境 (IDE) 以显示文件夹、 向导.vsz 文件和都与你的项目对话框中的模板文件的文本文件。 内容包括每个文件或文件夹的一条记录。 引用位置中的所有.vsdir 文件进行都合并，尽管只有一个.vsdir 文件通常用于描述多个文件夹、 向导、 或模板文件。

 文件夹 （子目录），用于在.vsdir 文件，而是.vsdir 文件本身中引用的文件位于同一目录中上。 IDE 运行向导或显示文件夹或文件中的时**新的项目**或**添加新项**对话框框中，IDE 会检查包含执行的文件，以确定是否.vsdir 文件的目录存在。 如果找到.vsdir 文件，IDE 将读取它以确定它是否包含执行或显示文件夹或文件的条目。 如果找到的项，IDE 在向导的执行或内容的显示中使用的信息。

 下面的代码示例摘自文件 SourceFiles.vsdir 中\<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems\Source_Files 注册表项：

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 在这种情况下，两条记录都位于一个文件。 换行符 （回车符） 用于分隔每个记录。 每行表示不同的文件类型。 管道 (&#124;) 字符用于分隔每个记录中的字段。 单个目录可以包含多个.vsdir 文件具有不同的文件的名称，或者可以具有一个.vsdir 文件为每个文件类型。

## <a name="fields"></a>字段
 下表列出了为每个记录指定的字段。

| 字段 | 描述 |
| - | - |
| 相对路径名称 (RelPathName) | 文件夹、 模板或.vsz 文件，如 HeaderFile.h 或 MyWizard.vsz 的名称。 此字段还可以用来表示的文件夹的名称。 |
| {clsidPackage} | 启用本地化字符串，如 LocalizedName、 描述、 IconResourceId 和 SuggestedBaseName，在 VSPackage 的附属动态链接库 (DLL) 资源的访问权限的 VSPackage 的 GUID。 如果未提供 DLLPath，IconResourceId 适用。 **注意：** 此字段是可选的除非一个或多个以前的字段是资源标识符。 此字段是一般不要本地化其文本的第三方向导与相对应的.vsdir 文件为空。 |
| LocalizedName | 向导的模板文件的本地化的名称。 此字段可以是字符串或窗体"#ResID"的资源标识符。 此名称显示在**添加新项**对话框。 **注意：** 如果 LocalizedName 资源标识符，则需要 {clsidPackage}。 |
| SortPriority | 一个整数，表示此模板文件或向导的相对优先级。 例如，如果此项的值为 1，此项是值为 1 和具有排序值为 2 或更大的所有项之前其他项旁边显示。<br /><br /> 排序优先级是相对于同一目录中的项。 在同一目录中可能有多个.vsdir 文件。 在这种情况下，从所有项<em>。</em>在该目录的 vsdir 文件进行合并。 具有相同优先级的项中的显示名称不区分大小写字典顺序列出。 `_wcsicmp`函数用于的项进行排序。<br /><br /> .Vsdir 文件中未描述的项包括一个大于.vsdir 文件中列出的最高优先级编号的优先级。 结果是列表的显示，而不考虑其名称末尾的这些项。 |
| 描述 | 向导的模板文件的本地化的说明。 此字段可以是字符串或窗体"#ResID"的资源标识符。 此字符串会显示**新的项目**或**添加新项**对话框中选择项目。 |
| DLLPath 或者 {clsidPackage} | 用于加载向导的模板文件的图标。 图标是使用 IconResourceId 加载作为带.dll 或.exe 文件的资源。 可以标识此.dll 或.exe 文件，使用完整路径或使用 VSPackage 的 GUID。 实现的 vspackage 的 DLL 用于加载图标 （不附属 DLL）。 |
| IconResourceId | 中的 DLL 或 VSPackage 的实现确定要显示的图标的 DLL 的资源标识符。 |
| 标志 (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>) | 用于禁用或启用**名称**并**位置**字段上**添加新项**对话框。 值**标志**字段是必需的位标志的组合的十进制等效值。<br /><br /> 当用户选择某个项上**新建**选项卡上，项目将决定是否名称字段和位置字段将显示当**添加新项**第一次显示对话框。 一个项，通过.vsdir 文件，可以控制仅选择项时是否将字段启用还是已禁用。 |
| SuggestedBaseName | 表示文件、 向导或模板的默认名称。 此字段是一个字符串或窗体"#ResID"的资源标识符。 IDE 使用此值以提供项的默认名称。 此基本值后追加一个整数值，以使名称唯一的例如 MyFile21.asp。<br /><br /> 在上一列表中，说明、 DLLPath、 IconResourceId、 标志和 SuggestedBaseNumber 仅适用于模板和向导文件。 这些字段不将应用于文件夹中。 BscPrjProjectItems 文件中的代码中阐释这一事实\<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems 注册表项。 此文件包含四个字段的每个记录具有三个记录 （一个用于每个文件夹）：RelPathName，{clsidPackage} LocalizedName 和 SortPriority。<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 当你创建的向导文件时，还应考虑以下问题。

- 没有有意义的数据的任何非必填的字段应作为占位符包含 0 （零）。

- 如果未不提供任何本地化的名称，向导文件中使用的相对路径名称。

- DLLPath 覆盖图标位置的 clsidPackage。

- 如果未定义图标，IDE 会替换该扩展的文件的默认图标。

- 如果未不提供任何建议的基名称，则使用项目。

- 如果您删除.vsz 文件、 文件夹或模板文件，还必须从.vsdir 文件删除其关联的记录。

## <a name="see-also"></a>请参阅
- [向导](../../extensibility/internals/wizards.md)
- [向导 (.Vsz) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)