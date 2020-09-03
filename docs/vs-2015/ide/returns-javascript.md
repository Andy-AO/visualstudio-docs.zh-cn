---
title: '&lt;返回 &gt; JavaScript)  (Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8fd8cdc8acdbf42b97e00f3c85647dd863721d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669951"
---
# <a name="ltreturnsgt-javascript"></a>&lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定函数或方法调用的结果的文档信息。

## <a name="syntax"></a>语法

```
<returns type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID" value="code">description
</returns>
```

#### <a name="parameters"></a>参数
 `type`（可选）。 返回值的数据类型。 类型可以是下列类型之一：

- ECMAScript 5 规范中的 ECMAScript 语言类型，例如 `Number` 和 `Object` 。

- DOM 对象，例如 `HTMLElement`、`Window` 和 `Document`。

- JavaScript 构造函数。

  `integer`（可选）。 如果 `type` 为 `Number` ，则指定返回值是否为整数。 设置为 `true` 以指示返回值为整数; 否则设置为 `false` 。 Visual Studio 不使用此属性以提供 IntelliSense 信息。

  `domElement`（可选）。 此属性已弃用；`type` 属性优先于此属性。 此属性指定所记录的返回值是否为 DOM 元素。 设置为 `true` 以指定返回值为 DOM 元素; 否则设置为 `false` 。 如果 `type` 未设置属性，并且 `domElement` 设置为，则 `true` `HTMLElement` 在执行语句完成时，IntelliSense 将记录的返回值视为。

  `mayBeNull`（可选）。 指定是否可以将记录的返回值设置为 null。 设置为 `true` 以指示返回值可以设置为 null; 否则设置为 `false` 。 默认值是 `false`。 Visual Studio 不使用此属性以提供 IntelliSense 信息。

  `elementType`（可选）。 如果 `type` 是 `Array`，此属性指定数组中元素的类型。

  `elementInteger`（可选）。 如果 `type` 是 `Array` 且 `elementType` 是 `Number`，此属性指定数组中的元素是否为整数。 设置为 `true`，指示数组中的元素都是整数；否则，设置为 `false`。 Visual Studio 不使用此属性以提供 IntelliSense 信息。

  `elementDomElement`（可选）。 此属性已弃用；`elementType` 属性优先于此属性。 如果 `type` 是 `Array`，此属性指定数组中的元素是否是 DOM 元素。 设置为 `true`，指定该元素是 DOM 元素；否则，设置为 `false`。 如果未指定 `elementType` 属性，且 `elementDomElement` 设置为 `true`，执行语句完成时，IntelliSense 将数组中的每个元素视为 `HTMLElement`。

  `elementMayBeNull`（可选）。 如果 `type` 是 `Array`，指定是否可将数组中的元素设置为 null。 设置为 `true`，指示数组中的元素可以设置为 null；否则，设置为 `false`。 默认值是 `false`。 Visual Studio 不使用此属性以提供 IntelliSense 信息。

  `locid`（可选）。 有关返回值的本地化信息的标识符。 标识符是成员 ID 或对应于 OpenAjax 元数据定义的消息绑定中的 `name` 属性值。 标识符类型取决于标记中指定的格式 [\<loc>](../ide/loc-javascript.md) 。

  `value`（可选）。 指定应计算以供 IntelliSense 使用的代码，而不是函数代码本身。 例如，可以使用此特性为异步回调提供 IntelliSense，如 `Promise` 。 将 `value` 属性与元素一起使用 `<returns>` 可以通过跳过长代码执行来提高 IntelliSense 性能。

  `description`（可选）。 返回值的说明。

## <a name="remarks"></a>备注
 `<returns>`元素必须位于函数体中的任何语句前面。

## <a name="example"></a>示例
 下面的代码示例演示如何使用 `<returns>` 元素。

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

// The following examples use the <remarks> element with a value attribute.

function getJson(complete) {
    /// <returns value='complete("")' ></returns>
    var r = new XMLHttpRequest();
    // . . .
}

getJson(function (json) {
    json.  // IntelliSense for a String object is
           // available here.
});

function calculate(x) {
    /// <returns value='1'/>
}
calculate().  // Completion list for a Number.

```

## <a name="see-also"></a>另请参阅
 [XML 文档注释](../ide/xml-documentation-comments-javascript.md)
