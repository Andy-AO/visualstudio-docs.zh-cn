---
title: 对函数行为进行批注
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _On_failure_
- _Return_type_success_
- _Always_
- _Maybe_raises_SEH_exception_
- _Raises_SEH_exception_
- _Called_from_function_class_
- _Function_class_
- _Must_inspect_result_
- _Success_
- _Check_return_
- _Use_decl_annotations_
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 78a8bf94323391d031aaf718f6e3132eb89e1df3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62560369"
---
# <a name="annotating-function-behavior"></a>对函数行为进行批注
除了对进行批注[函数参数和返回值](../code-quality/annotating-function-parameters-and-return-values.md)，可以批注整个函数的属性。

## <a name="function-annotations"></a>功能批注
 下列批注适用于整个函数，并描述了其行为或预期。

|批注|描述|
|----------------|-----------------|
|`_Called_from_function_class_(name)`|不是为了单独存在；相反，它是一个旨在与 `_When_` 批注一起使用的谓词。 有关详细信息，请参阅[指定时，并在其中批注应用](../code-quality/specifying-when-and-where-an-annotation-applies.md)。<br /><br /> `name`参数是任意字符串，也将出现在`_Function_class_`某些函数的声明中的批注。  `_Called_from_function_class_` 返回非零，如果当前正在分析的函数通过使用批注`_Function_class_`具有相同的值， `name`; 否则为它将返回零。|
|`_Check_return_`|批注一个返回值，并声明调用方应检查此值。 如果在 void 上下文中调用函数，则检查器将报告错误。|
|`_Function_class_(name)`|`name` 参数为由用户指定的任意字符串。  它存在于与其他命名空间不同的命名空间中。 函数、函数指针或（最有用）函数指针类型可指定为属于一个或多个函数类。|
|`_Raises_SEH_exception_`|根据 `_When_` 和 `_On_failure_` 条件，批注始终引发结构化异常处理程序 (SEH) 异常的函数。 有关详细信息，请参阅[指定时，并在其中批注应用](../code-quality/specifying-when-and-where-an-annotation-applies.md)。|
|`_Maybe_raises_SEH_exception_`|根据 `_When_` 和 `_On_failure_` 条件，批注可选择引发 SEH 异常的函数。|
|`_Must_inspect_result_`|批注所有输出值，包括返回值、参数和全局值。  如果随后不检查批注对象中的值，则分析器将报告错误。 “检查”包括是否用于条件表达式，可分配给输出参数或全局，或作为参数传递。  对于返回值，`_Must_inspect_result_` 暗指 `_Check_return_`。|
|`_Use_decl_annotations_`|可能用于在函数定义 （也称为函数体） 上替代的标头中的批注列表。  当`_Use_decl_annotations_`是相同的函数的范围内标头显示的批注使用像它们也会存在于具有定义`_Use_decl_annotations_`批注。|

## <a name="successfailure-annotations"></a>成功/失败批注
 函数可能会失败，此时，函数的结果可能不完整或与成功时的结果不同。  下面列表中的批注提供了表示失败行为的方法。  若要使用这些批注，您必须使它们能够确定成功；因此，需要 `_Success_` 批注。  请注意，`NTSTATUS` 和 `HRESULT` 已内置 `_Success_` 批注；但是，如果对 `_Success_` 或 `NTSTATUS` 指定自己的 `HRESULT` 批注，则它将重写内置批注。

|批注|描述|
|----------------|-----------------|
|`_Always_(anno_list)`|等效于 `anno_list _On_failure_(anno_list)`；也就是说，无论函数是否成功，`anno_list` 中的批注都适用。|
|`_On_failure_(anno_list)`|仅当同时使用 `_Success_` 来批注函数时使用，并通过 typedef 的 `_Return_type_success_` 以显式或隐式方式使用。 当 `_On_failure_` 批注位于函数参数或返回值上时，`anno_list` (anno) 中的每个批注的行为就像将其编码为 `_When_(!expr, anno)`，其中，`expr` 是所需 `_Success_` 批注的参数。 这意味着，`_Success_` 到所有后置条件的隐含应用并不适用于 `_On_failure_`。|
|`_Return_type_success_(expr)`|可以应用于 typedef。 表示将批注所有返回该类型并且不显式具有 `_Success_` 的所有函数，就像它们具有 `_Success_(expr)`。 `_Return_type_success_` 不能用于函数或函数指针类型。|
|`_Success_(expr)`|`expr` 是生成右值的表达式。 当 `_Success_` 批注位于函数声明或定义上时，函数上以及后置条件中的每个批注 (`anno`) 的行为就像它已编码为 `_When_(expr, anno)`。 `_Success_` 批注只能用于函数，而不能用于函数的参数或返回类型。 一个函数上最多可以有一个 `_Success_` 批注，并且不能位于任何 `_When_`、`_At_` 或 `_Group_` 中。 有关详细信息，请参阅[指定时，并在其中批注应用](../code-quality/specifying-when-and-where-an-annotation-applies.md)。|

## <a name="see-also"></a>请参阅

- [使用 SAL 批注以减少 C/C++ 代码缺陷](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [了解 SAL](../code-quality/understanding-sal.md)
- [对函数参数和返回值进行批注](../code-quality/annotating-function-parameters-and-return-values.md)
- [批注结构和类](../code-quality/annotating-structs-and-classes.md)
- [对锁定行为进行批注](../code-quality/annotating-locking-behavior.md)
- [指定何时以及在何处应用批注](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [内部函数](../code-quality/intrinsic-functions.md)
- [最佳做法和示例](../code-quality/best-practices-and-examples-sal.md)