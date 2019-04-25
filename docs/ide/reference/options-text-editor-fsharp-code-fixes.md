---
title: “选项”>“文本编辑器”>“F#”>“代码修复”
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bb9daee86fec058fca68740eaea3b9436e5570d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778536"
---
# <a name="options-text-editor-f-code-fixes"></a>“选项”>“文本编辑器”>“F#”>“代码修复”

使用“代码修复”选项页，可以指定有助于发现代码错误并提供解决方案的设置。 若要访问此选项页，请先依次选择“工具” > “选项”，再依次选择“文本编辑器” > “F#” > “代码修复”。

## <a name="code-fixes"></a>代码修复

- **简化名称（删除不必要的限定符）**

   如果你选中此复选框，工具就会在有（如对频繁使用的命名空间的成员）不必要的限定时，简化完全限定的名称。

- **始终将开语句置于顶级**

   如果你选中此复选框，并在代码中键入开语句，工具就会将它置于顶级。

- **删除未使用的开语句**

   如果你选中此复选框，工具就会删除当前文件中未使用的开语句。

- **分析是否有未使用的值并建议修复**

   如果你选中此复选框，工具就会识别代码中未使用的值。 然后，如果你将鼠标悬停在未使用的值之上，它就会提供值使用方法建议。

## <a name="see-also"></a>请参阅

- [“选项”对话框 ->“环境”->“常规”](../../ide/reference/general-environment-options-dialog-box.md)
- [使用 CodeLens 查找代码更改和其他历史记录](../../ide/find-code-changes-and-other-history-with-codelens.md)