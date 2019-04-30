---
title: SccEnumChangedFiles 函数 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db9bc2738e9a4d7cac0d57b9c613b7070f60baff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62802901"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles 函数
此函数将给定的本地文件的列表，确定哪些文件是不同于源代码代码管理数据库中的相应版本。

## <a name="syntax"></a>语法

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>参数
 pContext

[in]源控件插件上下文指针。

 hWnd

[in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。

 cFiles

[in]文件名称中指定的数量`lpFileNames`数组。 此外指定了大小的`plIsFileDifferent`数组。

 lpFileNames

[in]若要检查的本地文件名称的数组。

 plIsFileDifferent

[in、 out]值，该值指示每个文件的差异状态数组 (数组必须至少具有`cFiles`条目)。 该文件是不同的非零值表示。

## <a name="return-value"></a>返回值
 此函数的源控制插件实现应返回以下值之一：

|“值”|描述|
|-----------|-----------------|
|SCC_OK|操作已成功完成。|
|SCC_UNSPECIFIEDERROR|常规错误。|

## <a name="see-also"></a>请参阅
- [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)