---
title: IDebugClassField::GetDefaultIndexer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eaaddbe6bb223e8e2987f8310f1d8e08d5602a01
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206835"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
获取默认索引器的名称。

## <a name="syntax"></a>语法

```cpp
HRESULT GetDefaultIndexer( 
   BSTR* pbstrIndexer
);
```

```csharp
int GetDefaultIndexer(
   out string pbstrIndexer
);
```

## <a name="parameters"></a>参数
`pbstrIndexer` [out]返回包含的默认索引器的名称的字符串。

## <a name="return-value"></a>返回值
 如果成功，则返回 S_OK 或如果没有默认索引器，则返回 S_FALSE。 否则，返回错误代码。

## <a name="remarks"></a>备注
 一个类的默认索引器是属性，它被标记为`Default`数组访问的属性。 这是特定于[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]。 下面是一个示例中声明的默认索引器[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]以及如何使用它。

```vb
Imports System.Collections;

Public Class Class1
    Private myList as Hashtable

    Default Public Property Item(ByVal Index As Integer) As Integer
        Get
            Return CType(List(Index), Integer)
        End Get
        Set(ByVal Value As Integer)
            List(Index) = Value
        End Set
    End Property
End Class

Function GetItem(Index as Integer) as Integer
    Dim classList as Class1 = new Class1
    Dim value as Integer

    ' Access array through default indexer
    value = classList(2)

    ' Access array through explicit property
    value = classList.Item(2)

    Return value
End Function
```

## <a name="see-also"></a>请参阅
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)