---
title: IDiaSymbol::get_symTag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_symTag method
ms.assetid: 139a35bd-faeb-4878-be72-394dedfbb18f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bdd4ed102718a1c81be55c848a2d3c891c0ba99
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63400848"
---
# <a name="idiasymbolgetsymtag"></a>IDiaSymbol::get_symTag
检索符号类型分类器。

## <a name="syntax"></a>语法

```C++
HRESULT get_symTag ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>参数
 `pRetVal`

[out]返回一个值从[SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)枚举，用于指定符号类型分类器。

## <a name="return-value"></a>返回值
 如果成功，则返回`S_OK`; 否则为返回`S_FALSE`或错误代码。

> [!NOTE]
> 返回值为`S_FALSE`表示该属性不是可用于符号。

## <a name="example"></a>示例

```C++
IDiaSymbol* pType;
DWORD       tag = 0;
pType->get_symTag( &tag );
```

## <a name="see-also"></a>请参阅
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)