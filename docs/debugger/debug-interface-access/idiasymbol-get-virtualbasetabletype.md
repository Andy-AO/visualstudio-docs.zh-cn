---
title: IDiaSymbol::get_virtualBaseTableType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edbd1d8ae66e58611ab538cf0bfe695cb22b3412
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63400883"
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
检索的虚拟表，基指针的类型。

## <a name="syntax"></a>语法

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`pRetVal`|[out]返回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)指定基表的类型的对象。|

## <a name="return-value"></a>返回值
 如果成功，则返回`S_OK`; 否则为返回`S_FALSE`或错误代码。

> [!NOTE]
> 返回值为`S_FALSE`表示该属性不是可用于符号。

## <a name="remarks"></a>备注
 虚拟表，基指针 (`vbtptr`) 是中的隐藏的指针[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]vtable 处理从虚拟基类继承。 一个`vbtptr`可以具有不同的大小，具体取决于继承的类。

 此方法返回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)可用于确定 vbtptr 大小的对象。

## <a name="requirements"></a>要求

|需求|描述|
|-----------------|-----------------|
|标头：|dia2.h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>请参阅
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)