---
title: IDebugEngine2::SetMetric |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 325cd30a49fb636c56eebd9e6301b3999e851363
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920873"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
此方法设置名为指标的注册表值。

## <a name="syntax"></a>语法

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

#### <a name="parameters"></a>参数
 `pszMetric`

 [in]指标名称。

 `varValue`

 [in]指定的指标值。

## <a name="return-value"></a>返回值
 如果成功，则返回`S_OK`; 否则为返回错误代码。

## <a name="remarks"></a>备注
 指标是用于更改调试引擎的行为或播发受支持的功能的注册表值。 此方法可以将转发到相应的窗体调用[以便进行调试的 SDK 帮助程序](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)函数， `SetMetric`。

## <a name="see-also"></a>请参阅
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [用于调试的 SDK 帮助程序](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)