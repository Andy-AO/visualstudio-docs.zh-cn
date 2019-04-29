---
title: 'Idiasymbol:: Findchildren |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5199be7307fdaa607f5aa6a5f554d9fcc82f452d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837818"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
检索的符号的子级。

## <a name="syntax"></a>语法

```C++
HRESULT findChildren ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>参数
 `symtag`

[in]指定要检索的子对象的符号标记中定义[SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)。 设置为`SymTagNull`要检索的所有子级。

 `name`

[in]指定要检索的子对象的名称。 设置为`NULL`要检索的所有子级。

 `compareFlags`

[in]指定比较选项应用到匹配的名称。 中的值[NameSearchOptions 枚举](../../debugger/debug-interface-access/namesearchoptions.md)枚举可以单独或组合使用。

 `ppResult`

[out]返回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)检索包含子符号的列表的对象。

## <a name="return-value"></a>返回值
 返回`S_OK`如果至少一个子级的符号已找到，或者返回`S_FALSE`是否不发现了任何子级; 否则返回错误代码。

## <a name="remarks"></a>备注
 此方法等同于调用[idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)了该符号后的第一个参数的方法。

## <a name="see-also"></a>请参阅
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions 枚举](../../debugger/debug-interface-access/namesearchoptions.md)