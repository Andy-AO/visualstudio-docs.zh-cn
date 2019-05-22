---
title: 托管代码的代码分析警告（按 CheckId 排列）
ms.date: 04/18/2019
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1004
- CA1005
- CA1006
- CA1007
- CA1008
- CA1009
- CA1010
- CA1011
- CA1012
- CS1013
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1020
- CA1021
- CA1022
- CA1023
- CA1024
- CS1025
- CA1026
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1035
- CA1036
- CA1037
- CA1038
- CA1039
- CA1040
- CA1041
- CA1042
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1048
- CA1049
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1057
- CA1058
- CA1059
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1300
- CA1301
- CA1302
- CA1303
- CA1304
- CA1305
- CA1306
- CA1307
- CA1308
- CA1309
- CA1400
- CA1401
- CA1402
- CA1403
- CA1404
- CA1405
- CA1406
- CA1407
- CA1408
- CA1409
- CA1410
- CA1411
- CA1412
- CA1413
- CA1414
- CA1415
- CA1500
- CA1501
- CA1502
- CA1503
- CA1504
- CA1505
- CA1506
- CA1507
- CA1600
- CA1601
- CA1700
- CA1701
- CA1702
- CA1703
- CA1704
- CA1707
- CA1708
- CA1709
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- VA1716
- CA1717
- CA1719
- CA1720
- CA1721
- CA1722
- CA1723
- CA1724
- CA1725
- CA1726
- CA1727
- CA1728
- CA1729
- CA1730
- CA1800
- CA1801
- CA1802
- CA1803
- CA1804
- CA1806
- CA1809
- CA1810
- CA1811
- CA1812
- CA1813
- CA1814
- CA1815
- CA1816
- CA1819
- CA1820
- CA1821
- CA1822
- CA1823
- CA1824
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
- CA2007
- CA2100
- CA2101
- CA2102
- CA2103
- CA2104
- CA2105
- CA2106
- CA2107
- CA2108
- CA2109
- CA2110
- CA2111
- CA2112
- CA2114
- CA2115
- CA2116
- CA2117
- CA2118
- CA2119
- CA2120
- CA2121
- CA2122
- CA2123
- CA2124
- CA2126
- CA2127
- CA2128
- CA2129
- CA2130
- CA2131
- CA2132
- CA2133
- CA2134
- CA2135
- CA2136
- CA2137
- CA2138
- CA2139
- CA2140
- CA2141
- CA2142
- CA2143
- CA2144
- CA2145
- CA2146
- CA2147
- CA2148
- CA2149
- CA2150
- CA2151
- CA2200
- CA2201
- CA2202
- CA2204
- CA2205
- CA2207
- CA2208
- CA2210
- CA2211
- CA2212
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2218
- CA2219
- CA2220
- CA2221
- CA2222
- CA2223
- CA2224
- CA2225
- CA2226
- CA2228
- CA2229
- CA2227
- CA2230
- CA2231
- CA2232
- CA2233
- CA2234
- CA2235
- CA2236
- CA2237
- CA2238
- CA2239
- CA2240
- CA2241
- CA2242
- CA2243
- CA5122
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fabb7a7d0e13218532da40ce15d0f2661875b15e
ms.sourcegitcommit: 92a04c57ac0a49f304fa2ea5043436f30068c3cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2019
ms.locfileid: "65976176"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>按 checkid 排列的托管代码的代码分析警告

下表列出了托管代码的代码分析警告，按警告的 CheckId 标识符排列。

| CheckId | 警告 | 描述 |
|---------| - | - |
| CA1000 | [CA1000:不要在泛型类型中声明静态成员](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md) | 调用泛型类型的静态成员时，必须指定该类型的类型参数。 当调用不支持推理的泛型实例成员时，必须指定该成员的类型参数。 在上述两种情况下，用于指定类型参数的语法不同，但很容易混淆。 |
| CA1001 | [CA1001：具有可释放字段的类型应该是可释放的](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md) | 一个类声明并实现 System.IDisposable 类型的实例字段，但该类不实现 IDisposable。 声明 IDisposable 字段的类间接拥有非托管资源，并且应该实现 IDisposable 接口。 |
| CA1002 | [CA1002:不要公开泛型列表](../code-quality/ca1002-do-not-expose-generic-lists.md) | System.Collections.Generic.List < (的\<(T >) >) 是专为性能，不继承的泛型集合。 因此，List 不包含任何虚拟成员。 应改为公开针对继承设计的泛型集合。 |
| CA1003 | [CA1003:使用泛型事件处理程序实例](../code-quality/ca1003-use-generic-event-handler-instances.md) |一种类型包含一个委托，它返回 void，其签名包含两个参数 （一个的对象的第一个和第二个是分配给 EventArgs 的类型） 和包含程序集面向 Microsoft.NET Framework 2.0。 |
| CA1004 | [CA1004:泛型方法应提供类型参数](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md) | 推理是指由传递给泛型方法的自变量类型来确定该方法的类型参数，而不是显式指定类型参数。 若要启用推理，泛型方法的参数签名必须包含与该方法的类型参数属于相同类型的参数。 在这种情况下，不必指定类型参数。 如果对所有类型参数都使用推理，则调用泛型实例方法和非泛型实例方法的语法完全相同；这简化了泛型方法的可用性。 |
| CA1005 | [CA1005:避免泛型类型参数过多](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md) | 泛型类型包含的类型参数越多，越难以知道并记住每个类型参数各代表什么。 它是使用一个类型参数，如下所示列表通常明显\<T >，并在某些情况下有两个类型参数，如\<TKey，TValue >。 但是，如果存在两个以上的类型参数，则大多数用户都会感到过于困难。 |
| CA1006 | [CA1006:不要将嵌套在成员签名中的泛型类型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md) | 嵌套类型参数是一个类型参数，也是一个泛型类型。 若要调用签名包含嵌套类型参数的成员，用户必须实例化一个泛型类型，并将此类型传递到另一个泛型类型的构造函数。 所需的过程和语法很复杂，应当避免。 |
| CA1007 |[CA1007： 在适用处在适用处使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md) | 外部可见方法包含类型为 System.Object 的引用参数。 使用泛型方法使受约束的所有类型都可以传递给该方法，而比不先将类型强制转换为引用参数类型。 |
| CA1008 | [CA1008:枚举应具有零值](../code-quality/ca1008-enums-should-have-zero-value.md) | 像其他值类型一样，未初始化枚举的默认值为零。 无标志特性的枚举应通过使用零值来定义成员，这样默认值即为该枚举的有效值。 如果应用了 FlagsAttribute 特性的枚举定义值为零成员，则该成员的名称应为“None”，以指示枚举中尚未设置值。 |
| CA1009 | [CA1009:正确声明事件处理程序](../code-quality/ca1009-declare-event-handlers-correctly.md) | 事件处理程序方法采用两个参数。 第一个参数属于 System.Object 类型，名为“sender”。 它是引发事件的对象。 第二个参数属于 System.EventArgs 类型，名为“e”。 这是与该事件关联的数据。 事件处理程序方法不应返回值；在 C# 编程语言中，这由返回类型 void 指示。 |
| CA1010 | [CA1010:集合应实现泛型接口](../code-quality/ca1010-collections-should-implement-generic-interface.md) | 若要扩大集合的用途，应实现某个泛型集合接口。 然后，可以使用该集合来填充泛型集合类型。 |
| CA1011 |[CA1011:请考虑将基类型作为参数传递](../code-quality/ca1011-consider-passing-base-types-as-parameters.md) | 在方法声明中将基类型指定为参数时，可以将派生自基类型的任何类型作为相应的参数传递给方法。 如果不需要派生参数类型提供的其他功能，则使用基类型将使方法可以得到更广泛的使用。 |
| CA1012 | [CA1012:抽象类型不应具有构造函数](../code-quality/ca1012-abstract-types-should-not-have-constructors.md) | 抽象类型的构造函数只能由派生类型调用。 由于公共构造函数用于创建类型的实例，但无法为抽象类型创建实例，因此具有公共构造函数的抽象类在设计上是错误的。 |
| CA1013 | [CA1013:重载相等运算符，加法和减法](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md) | 公共或受保护类型实现加或减运算符时没有实现相等运算符。 |
| CA1014 | [CA1014:用 CLSCompliantAttribute 标记程序集](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md) | 公共语言规范 (CLS) 定义了程序集在跨编程语言使用时必须符合的命名限制、数据类型和规则。 好的设计要求所有程序集用 <xref:System.CLSCompliantAttribute> 显式指示 CLS 合规性。 如果程序集没有此特性，则该程序集即不合规。 |
| CA1016 | [CA1016:用 AssemblyVersionAttribute 标记程序集](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md) | .NET Framework 使用版本号唯一地标识程序集，以及如何绑定到强名称程序集中的类型。 版本号与版本和发行者策略一起使用。 默认情况下，仅使用用于生成应用程序的程序集版本运行应用程序。 |
| CA1017 | [CA1017:用 ComVisibleAttribute 标记程序集](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md) |ComVisibleAttribute 决定 COM 客户端如何访问托管代码。 合理的设计指出程序集将显式指示 COM 可见性。 可以设置整个程序集的 COM 可见性，然后重写各个类型和类型成员的 COM 可见性。 如果此特性不存在，则程序集的内容对 COM 客户端可见。 |
| CA1018 | [CA1018:用 AttributeUsageAttribute 标记特性](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md) | 当定义自定义特性时，用 AttributeUsageAttribute 标记该特性，以指示源代码中可以应用自定义特性的位置。 特性的含义和预定用法将决定它在代码中的有效位置。 |
| CA1019 | [CA1019:定义特性参数的访问器](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) | 特性可以定义强制自变量，在对目标应用该特性时必须指定这些自变量。 这些自变量也称为位置自变量，因为它们将作为位置参数提供给特性构造函数。 对于每一个强制自变量，特性还必须提供一个相应的只读属性，以便可以在执行时检索该自变量的值。 特性还可以定义可选自变量，可选自变量也称为命名自变量。 这些变量按名称提供给特性构造函数，并且必须具有相应的读/写属性。 |
| CA1020 | [CA1020:避免使用类型极少的命名空间](../code-quality/ca1020-avoid-namespaces-with-few-types.md) | 请确保每个命名空间都有一个逻辑组织，并确保将类型放入稀疏填充的命名空间的理由是有效的。 |
| CA1021 | [CA1021:避免使用 out 参数](../code-quality/ca1021-avoid-out-parameters.md) | 通过引用（使用 out 或 ref）传递类型要求具有使用指针的经验，了解值类型和引用类型的不同之处，以及能处理具有多个返回值的方法。 另外，out 和 ref 参数之间的差异没有得到广泛了解。 |
| CA1023 | [CA1023:索引器不应是多维](../code-quality/ca1023-indexers-should-not-be-multidimensional.md) | 索引器（即索引属性）应该使用一个索引。 多维索引器会大大降低库的可用性。 |
| CA1024 | [CA1024： 在适用处在适用处使用属性](../code-quality/ca1024-use-properties-where-appropriate.md) | 公共或受保护方法的名称以“Get”开头，没有采用任何参数或返回的值不是数组。 该方法可能很适于成为属性。 |
| CA1025 | [CA1025:用形参数组替换重复的实参](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md) | 如果参数的具体数量未知且变量参数为相同类型或可作为相同类型传递，请使用参数数组代替重复参数。 |
| CA1026 | [CA1026:不应使用默认参数](../code-quality/ca1026-default-parameters-should-not-be-used.md) | CLS 中允许使用默认参数的方法；但是 CLS 允许编译器忽略为这些参数分配的值。 为了跨编程语言维护所需的行为，必须使用提供默认参数的方法重载来替换使用默认参数的方法。 |
| CA1027 |[CA1027:用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md) | 枚举是一种值类型，它定义一组相关的已命名常数。 如果可以按照有意义的方式组合一个枚举的已命名常数，则对该枚举应用 FlagsAttribute。 |
| CA1028 | [CA1028:枚举存储应为 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md) | 枚举是一种值类型，它定义一组相关的已命名常数。 默认情况下，System.Int32 数据类型用于存储常量值。 尽管您可以更改此基础类型，然而对于大多数情况，既不需要，也不建议您这样做。 |
| CA1030 | [CA1030： 在适用处在适用处使用事件](../code-quality/ca1030-use-events-where-appropriate.md) |该规则检测名称通常用于事件的方法。 如果为响应明确定义的状态更改而调用一个方法，则应由事件处理程序调用该方法。 调用该方法的对象应引发事件而不是直接调用该方法。 |
| CA1031 | [CA1031:不要捕捉一般异常类型](../code-quality/ca1031-do-not-catch-general-exception-types.md) | 不应捕捉一般异常。 捕捉更具体的异常，或者在执行 catch 块中的最后一条语句时重新引发一般异常。 |
| CA1032 |[CA1032:实现标准异常构造函数](../code-quality/ca1032-implement-standard-exception-constructors.md) | 如果不能提供完整的构造函数集，要正确处理异常将变得比较困难。 |
| CA1033 | [CA1033:接口方法应可由子类型调用](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md) | 未密封的外部可见类型提供了显式实现公共接口的方法，但没有提供具有相同名称的其他外部可见方法。 |
| CA1034 | [CA1034:嵌套的类型不应是可见](../code-quality/ca1034-nested-types-should-not-be-visible.md) | 嵌套类型是在另一个类型的范围中声明的类型。 嵌套类型用于封装包含类型的私有实现详细信息。 如果用于此用途，则嵌套类型不应是外部可见的。 |
| CA1035 | [CA1035:ICollection 实现含有强类型成员](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md) | 此规则要求 ICollection 实现提供强类型成员，以使用户在使用该接口提供的功能时不必将自变量强制转换成 Object 类型。 此规则假定实现 ICollection 的类型这样做是为了管理其类型强于对象的实例的集合。 |
| CA1036 | [CA1036:重写可比较类型的方法](../code-quality/ca1036-override-methods-on-comparable-types.md) |公共或受保护类型实现 System.IComparable 接口。 它不重写 Object.Equals，也不重载表示相等、不等、小于或大于的语言特定运算符。 |
| CA1038 | [CA1038:枚举数应强类型化](../code-quality/ca1038-enumerators-should-be-strongly-typed.md) | 此规则要求 IEnumerator 实现还提供 Current 属性的强类型版本，以使用户在使用该接口提供的功能时不必将返回值强制转换为强类型。 |
| CA1039 | [CA1039:列表已强类型化](../code-quality/ca1039-lists-are-strongly-typed.md) | 此规则要求 IList 实现提供强类型成员，以使用户在使用该接口提供的功能时不必将自变量强制转换成 System.Object 类型。 |
| CA1040 |[CA1040:避免使用空接口](../code-quality/ca1040-avoid-empty-interfaces.md) | 接口定义提供某个行为或使用协定的成员。 接口所描述的功能可以被任何类型采用，而不管该类型出现在继承层次结构中的哪个位置。 类型通过实现接口的成员来实现接口。 空接口无法定义任何成员；因此，它无法定义可以实现的协定。 |
| CA1041 | [CA1041:提供 ObsoleteAttribute 消息](../code-quality/ca1041-provide-obsoleteattribute-message.md) | 用未指定其 ObsoleteAttribute.Message 属性的 System.ObsoleteAttribute 特性来标记类型或成员。 当编译用 ObsoleteAttribute 标记的类型或成员时，将显示该特性的 Message 属性。 这将为用户提供有关已过时的类型或成员的信息。 |
| CA1043 | [CA1043:使用整型或字符串参数用于索引器](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md) | 索引器（即索引属性）应将整型或字符串类型用于索引。 这些类型一般用于为数据结构编制索引，并且提高库的可用性。 应仅限于在设计时无法指定特定整型或字符串类型的情况下使用 Object 类型。 |
| CA1044 | [CA1044:属性不应是只写的](../code-quality/ca1044-properties-should-not-be-write-only.md) | 虽然可以接受且经常需要使用只读属性，但设计准则禁止使用只写属性。 这是因为允许用户设置值但又禁止该用户查看这个值不能提供任何安全性。 而且，如果没有读访问，将无法查看共享对象的状态，使其用处受到限制。 |
| CA1045 |[CA1045:不要通过引用来传递类型](../code-quality/ca1045-do-not-pass-types-by-reference.md) | 通过引用（使用 out 或 ref）传递类型要求具有以下能力：使用指针的经验，了解值类型和引用类型的不同之处，以及能处理具有多个返回值的方法。 库设计为普通用户不应指望用户掌握了架构师`out`或`ref`参数。 |
| CA1046 | [CA1046:请重载相等运算符对引用类型](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md) | 对于引用类型，相等运算符的默认实现几乎始终是正确的。 默认情况下，仅当两个引用指向同一对象时，它们才相等。 |
| CA1047 |[CA1047:不要声明在密封类型中的受保护的成员](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md) | 类型声明受保护的成员，使继承类型可以访问或重写该成员。 按照定义，不能继承密封类型，这表示不能调用密封类型上的受保护方法。 |
| CA1048 | [CA1048:不要声明在密封类型中的虚拟成员](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md) | 类型将方法声明为虚方法，使继承类型可以重写虚方法的实现。 按照定义，不能继承密封类型。 这使得虚方法对于密封类型没有意义。 |
| CA1049 | [CA1049:拥有本机资源的类型应是可释放的](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md) | 分配非托管资源的类型应该实现 IDisposable，以使调用方可以根据需要释放这些资源，并缩短持有这些资源的对象的生存期。 |
| CA1050 | [CA1050:在命名空间中声明类型](../code-quality/ca1050-declare-types-in-namespaces.md) | 应在命名空间内声明类型以避免名称冲突，并作为一种在对象层次结构中组织相关类型的方式。 |
| CA1051 | [CA1051:不要声明可见实例字段](../code-quality/ca1051-do-not-declare-visible-instance-fields.md) | 字段的主要用途应是作为实现的详细信息。 字段应为 private 或 internal，并应通过使用属性公开这些字段。 |
| CA1052 | [CA1052:应密封静态容器类型](../code-quality/ca1052-static-holder-types-should-be-sealed.md) | 公共或受保护类型仅包含静态成员，而且没有用 sealed（C# 参考）(NotInheritable) 修饰符声明该类型。 应使用 sealed 修饰符标记不希望被继承的类型，以免将其用作基类型。 |
| CA1053 |[CA1053:静态容器类型不应具有构造函数](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md) | 公共或嵌套公共类型只声明了静态成员，但具有公共或受保护的默认构造函数。 由于调用静态成员不需要类型的示例，因此没必要使用构造函数。 为安全起见，字符串重载应使用字符串自变量调用统一资源标识符 (URI) 重载。 |
| CA1054 | [CA1054:URI 参数不应为字符串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md) | 如果某方法采用 URI 的字符串表示形式，则应提供采用 URI 类的实例的相应重载，该重载以安全的方式提供这些服务。 |
| CA1055 | [CA1055:URI 返回值不应为字符串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md) | 此规则假定该方法返回 URI。 URI 的字符串表示形式容易导致分析和编码错误，并且可造成安全漏洞。 System.Uri 类以一种安全的方式提供这些服务。 |
| CA1056 | [CA1056:URI 属性不应为字符串](../code-quality/ca1056-uri-properties-should-not-be-strings.md) | 此规则假定属性表示统一资源标识符 (URI)。 URI 的字符串表示形式容易导致分析和编码错误，并且可造成安全漏洞。 System.Uri 类以一种安全的方式提供这些服务。 |
| CA1057 | [CA1057:字符串 URI 重载调用 System.Uri 重载](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md) | 某个类型声明的方法重载与 System.Uri 参数仅在字符串参数的放置方面有所不同。 采用字符串参数的重载不调用采用 URI 参数的重载。 |
| CA1058 | [CA1058:类型不应扩展某些基类型](../code-quality/ca1058-types-should-not-extend-certain-base-types.md) | 外部可见的类型扩展某些基类型。 请使用某个备选项。 |
| CA1059 |[CA1059:成员不应公开某些具体类型](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md) | 具体类型是指具有一个完整实现因此可以实例化的类型。 若要使成员可以得到广泛使用，请使用建议的接口来替换具体类型。 |
| CA1060 | [CA1060:将 P/Invoke 移动到 NativeMethods 类](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md) | 平台调用方法（例如标以 System.Runtime.InteropServices.DllImportAttribute 特性的那些方法，或在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中使用 Declare 关键字定义的方法）可以访问非托管代码。 这些方法应属于 NativeMethods、SafeNativeMethods 或 UnsafeNativeMethods 类。 |
| CA1061 |[CA1061:不要隐藏基类方法](../code-quality/ca1061-do-not-hide-base-class-methods.md) | 如果派生方法的参数签名只是在类型方面有所不同，而且与基方法的参数签名中的对应类型相比，这些类型的派生方式更弱，则基类型中的方法由派生类型中的同名方法隐藏。 |
| CA1062 | [CA1062:验证公共方法的参数](../code-quality/ca1062-validate-arguments-of-public-methods.md) | 对于传递给外部可见方法的所有引用自变量，都应检查其是否为 null。 |
| CA1063 | [CA1063:正确实现 IDisposable](../code-quality/ca1063-implement-idisposable-correctly.md) | 所有的 IDisposable 类型都应当正确实现 Dispose 模式。 |
| CA1064 | [CA1064:异常应该是公共的](../code-quality/ca1064-exceptions-should-be-public.md) | 内部异常仅在其自己的内部范围内可见。 当异常超出内部范围后，只能使用基异常来捕获该异常。 如果内部异常继承自<xref:System.Exception>， <xref:System.SystemException>，或<xref:System.ApplicationException>，外部代码将没有足够的信息来了解应如何处理异常。 |
| CA1065 | [CA1065:不会引发意外的位置中的异常](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | 不应引发异常的方法引发了异常。 |
| CA1300 | [CA1300:指定 MessageBoxOptions](../code-quality/ca1300-specify-messageboxoptions.md) | 为了让使用从右到左阅读顺序的文化区域正确显示消息框，必须将 MessageBoxOptions 枚举的 RightAlign 和 RtlReading 成员传递给 Show 方法。 |
| CA1301 | [CA1301:避免快捷键重复](../code-quality/ca1301-avoid-duplicate-accelerators.md) | 访问键也称为快捷键，它通过使用 Alt 键来实现对控件的键盘访问。 如果多个控件具有重复的访问键，则访问密钥的行为不明确。 |
| CA1302 | [CA1302:请不要对区域设置特定字符串](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md) | System.Environment.SpecialFolder 枚举包含表示特殊系统文件夹的成员。 对于不同的操作系统，这些文件夹的位置可能具有不同的值；用户也可能会更改某些位置；或者这些位置已经进行了本地化。 Environment.GetFolderPath 方法返回与 Environment.SpecialFolder 枚举关联、经过本地化且与当前正在运行的计算机相应的位置。 |
| CA1303 | [CA1303:不要将文本作为本地化参数传递](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md) | 外部可见方法将字符串作为参数传递给构造函数或.NET Framework 类库中的方法，该字符串应该是可本地化。 |
| CA1304 | [CA1304:指定 CultureInfo](../code-quality/ca1304-specify-cultureinfo.md) | 某方法或构造函数调用的成员有一个接受 System.Globalization.CultureInfo 参数的重载，但该方法或构造函数没有调用接受 CultureInfo 参数的重载。 如果未提供 CultureInfo 或 System.IFormatProvider 对象，则重载成员提供的默认值可能不会在所有区域设置中产生您想要的效果。 |
| CA1305 | [CA1305:指定 IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md) | 某方法或构造函数调用的一个或多个成员有接受 System.IFormatProvider 参数的重载，但该方法或构造函数没有调用接受 IFormatProvider 参数的重载。 如果未提供 System.Globalization.CultureInfo 或 IFormatProvider 对象，则重载成员提供的默认值可能不会在所有区域设置中产生您想要的效果。 |
| CA1306 | [CA1306:设置区域设置的数据类型](../code-quality/ca1306-set-locale-for-data-types.md) | 区域设置决定数据的区域性特定显示元素，例如，数值、货币符号和排序顺序所用的格式。 在创建 DataTable 或 DataSet 时，应显式设置区域设置。 |
| CA1307 | [CA1307:指定 StringComparison](../code-quality/ca1307-specify-stringcomparison.md) | 字符串比较运算使用不设置 StringComparison 参数的方法重载。 |
| CA1308 |[CA1308:将字符串规范化为大写](../code-quality/ca1308-normalize-strings-to-uppercase.md) | 字符串应正常化为大写字母。 少量字符转换为小写字母后不能再转换回来。 |
| CA1309 | [CA1309:使用序号 StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md) | 非语义的字符串比较运算不会将 StringComparison 参数设置为 Ordinal 或 OrdinalIgnoreCase。 因此，通过将参数显式设置为 StringComparison.Ordinal 或 StringComparison.OrdinalIgnoreCase，通常可以提高代码的速度、正确性和可靠性。 |
| CA1400 | [CA1400:P/Invoke 入口点应该存在](../code-quality/ca1400-p-invoke-entry-points-should-exist.md) |公共或受保护方法标有 System.Runtime.InteropServices.DllImportAttribute 特性。 未能找到非托管库，或者未能将方法与库中的函数匹配。 |
| CA1401 | [CA1401:P/Invokes 应该是不可见](../code-quality/ca1401-p-invokes-should-not-be-visible.md) | 公共类型中的公共或受保护方法具有 System.Runtime.InteropServices.DllImportAttribute 特性（还在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中由 Declare 关键字实现）。 这些方法不能公开。 |
| CA1402 |[CA1402:避免在 COM 可见接口中的重载](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md) | 在向 COM 客户端公开重载的方法时，只有第一个方法重载保留其名称。 对于后续重载，将为其指定唯一名称，方法是在其名称后面追加一个下划线字符 (_) 和一个与该重载的声明顺序对应的整数。 |
| CA1403 | [CA1403:自动布局类型不应对 COM 可见](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md) | 某个 COM 可见的值类型用设置为 LayoutKind.Auto 的 System.Runtime.InteropServices.StructLayoutAttribute 特性标记。这些类型的布局可以更改.NET Framework 中，将中断要求特定布局的 COM 客户端的不同版本之间。 |
| CA1404 | [CA1404:紧接在 P/Invoke 之后调用 GetLastError](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md) | 调用了 Marshal.GetLastWin32Error 方法或等效[!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)]GetLastError 函数，并紧位于前面的调用不为操作系统调用方法。 |
| CA1405 | [CA1405:COM 可见类型的基类型应对 COM 可见](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md) | 某个 COM 可见的类型是从非 COM 可见的类型派生而来。 |
| CA1406 |[CA1406:避免对 Visual Basic 6 客户端的 Int64 参数](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md) | Visual Basic 6 COM 客户端不能访问 64 位整数。 |
| CA1407 |[CA1407:避免在 COM 可见类型中的静态成员](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md) | COM 不支持静态方法。 |
| CA1408 | [CA1408:不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md) | 使用双重接口的类型使客户端可以绑定到特定的接口布局。 如果在将来的版本中对该类型或任何基类型的布局进行更改，将中断绑定到该接口的 COM 客户端。 默认情况下，如果未指定 ClassInterfaceAttribute 特性，则使用仅支持调度的接口。 |
| CA1409 | [CA1409:Com 可见类型应该是可创建对象](../code-quality/ca1409-com-visible-types-should-be-creatable.md) |专门标记为对 COM 可见的某个引用类型包含公共的参数化构造函数，但不包含公共的默认（无参数）构造函数。 没有公共默认构造函数的类型不能由 COM 客户端创建。 |
| CA1410 | [CA1410:应对 COM 注册方法进行匹配](../code-quality/ca1410-com-registration-methods-should-be-matched.md) | 某个类型声明了用 System.Runtime.InteropServices.ComRegisterFunctionAttribute 特性标记的方法，但没有声明用 System.Runtime.InteropServices.ComUnregisterFunctionAttribute 特性标记的方法，或相反。 |
| CA1411 | [CA1411:COM 注册方法应该是不可见](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md) | 用 System.Runtime.InteropServices.ComRegisterFunctionAttribute 特性或 System.Runtime.InteropServices.ComUnregisterFunctionAttribute 特性标记的方法在外部可见。 |
| CA1412 | [CA1412:将 ComSource 接口标记为 IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md) | 某个类型用 System.Runtime.InteropServices.ComSourceInterfacesAttribute 特性标记，并且至少一个指定的接口未用设置为 ComInterfaceType.InterfaceIsIDispatch 的 System.Runtime.InteropServices.InterfaceTypeAttribute 特性标记。 |
| CA1413 | [CA1413:避免在 COM 可见值类型中的非公共字段](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | 对 COM 可见的值类型的非公共实例字段对 COM 客户端可见。 请检查各个字段的内容以查找不应当公开的信息或将对设计或安全性造成意外影响的信息。 |
| CA1414 | [CA1414:标记用 MarshalAs 布尔型 P/Invoke 参数](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | Boolean 数据类型在非托管代码中有多种表示形式。 |
| CA1415 | [CA1415:正确声明 P/Invoke](../code-quality/ca1415-declare-p-invokes-correctly.md) | 此规则查找针对 [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] 函数的操作系统调用方法声明，这些函数具有指向 OVERLAPPED 结构参数的指针，而对应的托管参数不是指向 System.Threading.NativeOverlapped 结构的指针。 |
| CA1500 | [CA1500:变量名不应与字段名称](../code-quality/ca1500-variable-names-should-not-match-field-names.md) | 实例方法声明一个名称与声明类型的实例字段匹配的参数或局部变量，从而导致错误。 |
| CA1501 | [CA1501:避免过度继承](../code-quality/ca1501-avoid-excessive-inheritance.md) | 类型在继承层次结构中的深度超过四级。 深度嵌套的类型层次结构可能很难遵循、理解和维护。 |
| CA1502 | [CA1502:避免过度复杂](../code-quality/ca1502-avoid-excessive-complexity.md) | 此规则通过方法来测量线性独立的路径的数量，该数量是由条件分支的数量和复杂度决定的。 |
| CA1504 | [CA1504:检查令人误解的字段名](../code-quality/ca1504-review-misleading-field-names.md) | 实例字段的名称以"s_"开头或静态 (在 Visual Basic 中的为 Shared) 字段的名称以"m_"开头。 |
| CA1505 | [CA1505:避免编写无法维护的代码](../code-quality/ca1505-avoid-unmaintainable-code.md) | 类型或方法具有较低的可维护性索引值。 如果可维护性指数较低，则表示类型或方法可能难以维护，最好重新进行设计。 |
| CA1506 |[CA1506:避免过度类耦合](../code-quality/ca1506-avoid-excessive-class-coupling.md) | 此规则通过计算类型或方法包含的唯一类型引用的个数来衡量类耦合。 |
| CA1600 | [CA1600:不要使用 idle 进程优先级](../code-quality/ca1600-do-not-use-idle-process-priority.md) | 不要将进程优先级设置为 Idle。 具有 System.Diagnostics.ProcessPriorityClass.Idle 优先级的进程将在 CPU 本应处于空闲状态时占用它，从而阻止进入待机状态。 |
| CA1601 | [CA1601:不要使用阻止电源状态更改的计时器](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md) | 频率较高的定期活动会使 CPU 处于繁忙状态，并且会干扰具有节能功能（关闭显示器和硬盘）的空闲计时器。 |
| CA1700 | [CA1700:未命名的枚举值 Reserved](../code-quality/ca1700-do-not-name-enum-values-reserved.md) | 此规则假定当前不使用名称中包含“reserved”的枚举成员，而是将其作为一个占位符，以在将来的版本中重命名或移除它。 重命名或移除成员是一项重大更改。 |
| CA1701 | [CA1701:资源字符串复合词应采用正确的大小写](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md) | 资源字符串中的每个单词根据大小写被拆分为标记。 Microsoft 拼写检查器库会对由两个连续的标记构成的每个组合进行检查。 如果被识别，该单词将生成规则冲突。 |
| CA1702 | [CA1702:复合词应采用正确的大小写](../code-quality/ca1702-compound-words-should-be-cased-correctly.md) | 标识符的名称包含多个单词，其中至少有一个单词似乎是大小写不正确的组合词。 |
| CA1703 | [CA1703:资源字符串应正确拼写](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md) | 资源字符串包含一个或多个未被 Microsoft 拼写检查器库识别的单词。 |
| CA1704 | [CA1704:标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md) | 外部可见标识符的名称中包含一个或多个未被 Microsoft 拼写检查器库识别的单词。 |
| CA1707 | [CA1707:标识符不应包含下划线](../code-quality/ca1707-identifiers-should-not-contain-underscores.md) | 按照约定，标识符名称不包含下划线 (_) 字符。 该规则将检查命名空间、类型、成员和参数。 |
| CA1708 | [CA1708:标识符不应不同于用例的详细信息](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md) | 不能仅通过大小写区分命名空间、类型、成员和参数的标识符，因为针对公共语言运行时的语言不需要区分大小写。 |
| CA1709 | [CA1709:标识符应采用正确的大小写](../code-quality/ca1709-identifiers-should-be-cased-correctly.md) | 按照约定，参数名使用 Camel 大小写，命名空间、类型和成员名称使用 Pascal 大小写。 |
| CA1710 | [CA1710:标识符应具有正确的后缀](../code-quality/ca1710-identifiers-should-have-correct-suffix.md) |按照约定，扩展某些基类型或实现某些接口的类型的名称，或者由这些类型派生的类型的名称应具有与相应基类型或接口关联的后缀。 |
| CA1711 | [CA1711:标识符应采用正确的后缀](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md) | 按照约定，只有扩展某些基类型或实现某些接口的类型的名称或者从这些类型派生的类型的名称，应该以特定的保留后缀结尾。 其他类型名称不应使用这些保留的后缀。 |
| CA1712 | [CA1712:不要使用类型名称的枚举值的前缀](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md) | 枚举成员的名称不能使用类型名称作为前缀，因为类型信息将由开发工具提供。 |
| CA1713 | [CA1713:事件不应具有 before 或 after 前缀](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md) | 事件的名称以“Before”或“After”开头。 若要命名按特定顺序引发的相关事件，请使用现在时或过去时指示一系列操作中的相对位置。 |
| CA1714 | [CA1714:枚举应采用复数形式的名称](../code-quality/ca1714-flags-enums-should-have-plural-names.md) | 公共枚举具有 System.FlagsAttribute 特性并且其名称不是以“s”结尾。 用 FlagsAttribute 标记的类型具有复数形式的名称，因为该特性指明可以指定多个值。 |
| CA1715 | [CA1715:标识符应具有正确的前缀](../code-quality/ca1715-identifiers-should-have-correct-prefix.md) | 外部可见的接口的名称不以大写的“I”开头。 外部可见的类型或方法上的泛型类型参数的名称不以大写的“T”开头。 |
| CA1716 | [CA1716:标识符不应与关键字](../code-quality/ca1716-identifiers-should-not-match-keywords.md) | 某个命名空间名称或类型名称与编程语言中的保留关键字相同。 命名空间和类型的标识符不应与针对公共语言运行时的语言所定义的关键字冲突。 |
| CA1717 | [CA1717:只有 FlagsAttribute 枚举应采用复数形式的名称](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md) | 命名约定规定，复数形式的枚举名称表示可以同时指定多个枚举值。 |
| CA1719 | [CA1719:参数名不应与成员名称](../code-quality/ca1719-parameter-names-should-not-match-member-names.md) | 参数名称应传达参数的含义，成员名称应传达成员的含义。 两者相同的设计非常少见。 使参数与其成员同名会导致不直观的效果，会使库难以使用。 |
| CA1720 |[CA1720:标识符不应包含类型名称](../code-quality/ca1720-identifiers-should-not-contain-type-names.md) | 外部可见成员中的某个参数的名称包含一个数据类型名称，或者外部可见成员的名称包含一个语言特定的数据类型名称。 |
| CA1721 | [CA1721:属性名不应与 get 方法](../code-quality/ca1721-property-names-should-not-match-get-methods.md) |公共或受保护成员的名称以“Get”开头，且其余部分与公共或受保护属性的名称匹配。 “Get”方法和属性的名称应能够明确区分其功能上的差异。 |
| CA1722 | [CA1722:标识符应采用正确的前缀](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md) | 按照约定，只有某些编程元素具有以特定前缀开头的名称。 |
| CA1724 | [CA1724:类型名不应与命名空间](../code-quality/ca1724-type-names-should-not-match-namespaces.md) | 类型名不应与在.NET Framework 类库中定义的命名空间的名称。 与该规则冲突将使库的可用性下降。 |
| CA1725 | [CA1725:参数名应与基声明](../code-quality/ca1725-parameter-names-should-match-base-declaration.md) | 以一致的方式命名重写层次结构中的参数可以提高方法重写的可用性。 如果派生方法中的参数名与基声明中的名称不同，可能会导致无法区分出该方法是基方法的重写还是该方法的新重载。 |
| CA1726 | [CA1726:使用首选的词条](../code-quality/ca1726-use-preferred-terms.md) | 在外部可见的标识符的名称中，包括一个存在首选备用词条的词条。 或者，名称中包含“Flag”或“Flags”一词。 |
| CA1800 | [CA1800： 避免进行不必要的强制转换](../code-quality/ca1800-do-not-cast-unnecessarily.md) | 重复强制转换会降低性能，特别是在精简的迭代语句中执行强制转换时。 |
| CA1801 | [CA1801:检查未使用的参数](../code-quality/ca1801-review-unused-parameters.md) | 方法签名包含一个没有在方法体中使用的参数。 |
| CA1802 |[CA1802:在适用处使用文本](../code-quality/ca1802-use-literals-where-appropriate.md) |某个字段被声明为 static 和 read-only（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 Shared 和 ReadOnly），并使用可在编译时计算的值初始化。 因为分配给目标字段的值可在编译时，将声明更改为一个常量 (中的常量[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 字段，以便在编译时而不是在运行时计算的值。 |
| CA1804 | [CA1804:删除未使用的局部变量](../code-quality/ca1804-remove-unused-locals.md) | 未使用的局部变量和不必要的赋值会增加程序集的大小并降低性能。 |
| CA1806 | [CA1806:不要忽略方法结果](../code-quality/ca1806-do-not-ignore-method-results.md) | 创建一个新对象，但从不使用该对象；或者调用会创建并返回一个新字符串的方法，但从不使用这个新字符串；或者 COM 或 P/Invoke 方法返回一个从不使用的 HRESULT 或错误代码。 |
| CA1809 |[CA1809:避免过多的局部变量](../code-quality/ca1809-avoid-excessive-locals.md) | 优化性能的常见方法是将值存储于处理器寄存器，而不是内存中，这称为“注册值”。 若要增加所有本地变量都是以内的机会，限制为 64 的本地变量的数目。 |
| CA1810 | [CA1810:引用类型的静态字段以内联方式初始化](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md) | 当一个类型声明显式静态构造函数时，实时 (JIT) 编译器会向该类型的每个静态方法和实例构造函数中添加一项检查，以确保之前已调用该静态构造函数。 静态构造函数检查会降低性能。 |
| CA1811 | [CA1811:避免使用未调用的私有代码](../code-quality/ca1811-avoid-uncalled-private-code.md) | 某个私有或内部（程序集级别）成员在程序集中没有调用方，既不是由公共语言运行时调用的，也不是由委托调用的。 |
| CA1812 | [CA1812:避免未实例化的内部类](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md) | 程序集级别类型的实例不是由程序集中的代码创建的。 |
| CA1813 | [CA1813:避免使用未密封的特性](../code-quality/ca1813-avoid-unsealed-attributes.md) | .NET Framework 类库提供用于检索自定义特性的方法。 默认情况下，这些方法搜索特性继承层次结构。 通过密封特性，将无需搜索继承层次结构，且能够提高性能。 |
| CA1814 | [CA1814： 与通过多维首选使用交错的数组](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md) | 交错数组是元素为数组的数组。 构成元素的数组可以是不同的大小，以减少某些数据集的浪费空间。 |
| CA1815 | [CA1815:替代值类型上的 Equals 和相等运算符](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md) | 对于值类型，Equals 的继承的实现使用反射库，并比较所有字段的内容。 反射需要消耗大量计算资源，可能没有必要比较每一个字段是否相等。 如果希望用户对实例进行比较或排序，或者希望用户将实例用作哈希表键，则值类型应实现 Equals。 |
| CA1816 | [CA1816:调用 GC。SuppressFinalize 正确](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md) | 实现 Dispose 方法不会调用 GC。SuppressFinalize;或不是实现 Dispose 方法调用 GC。SuppressFinalize;或使用方法调用 GC。SuppressFinalize 和传递内容以外此 （我在 Visual Basic 中）。 |
| CA1819 | [CA1819:属性不应返回数组](../code-quality/ca1819-properties-should-not-return-arrays.md) | 即使属性是只读的，该属性返回的数组也不是写保护的。 若要使数组不会被更改，属性必须返回数组的副本。 通常，用户不能理解调用这种属性的负面性能影响。 |
| CA1820 | [CA1820:测试有空字符串，使用字符串长度](../code-quality/ca1820-test-for-empty-strings-using-string-length.md) | 使用 String.Length 属性或 String.IsNullOrEmpty 方法比较字符串要比使用 Equals 的速度快得多。 |
| CA1821 | [CA1821：移除空终结器](../code-quality/ca1821-remove-empty-finalizers.md) | 应尽可能避免终结器，因为跟踪对象生存期会产生额外的性能系统开销。 空的终结器只会徒增系统开销，没有一点好处。 |
| CA1822 |[CA1822:将成员标记为静态](../code-quality/ca1822-mark-members-as-static.md) | 可以将不访问实例数据或不调用实例方法的成员标记为 static（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 Shared）。 在将这些方法标记为 static 之后，编译器将向这些成员发出非虚拟调用站点。 这会使性能敏感的代码的性能得到显著提高。 |
| CA1823 | [CA1823:避免未使用的私有字段](../code-quality/ca1823-avoid-unused-private-fields.md) | 检测到程序集内有似乎未访问过的私有字段。 |
| CA1824 |[CA1824:用 NeutralResourcesLanguageAttribute 标记程序集](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md) | NeutralResourcesLanguage 特性通知资源管理器的语言，用于显示非特定区域性的资源的程序集。 这将改进所加载的第一个资源的查找性能，并缩小工作集。 |
| CA1900 | [CA1900:值类型字段应为可移植](../code-quality/ca1900-value-type-fields-should-be-portable.md) | 此规则对以下项进行检查：当用显式布局声明的结构封送到 64 位操作系统上的非托管代码时，是否正确对齐。 |
| CA1901 | [CA1901:P/Invoke 声明应为可移植](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md) | 此规则计算 P/Invoke 的每个参数和返回值的大小，还验证它们在封送到 32 位和 64 位操作系统上的非托管代码时参数的大小是否正确。 |
| CA1903 | [CA1903:使用仅目标框架中的 API](../code-quality/ca1903-use-only-api-from-targeted-framework.md) | 一个成员或类型使用了某个 Service Pack 中引入的成员或类型，该 Service Pack 没有与项目的目标框架一起包括。 |
| CA2000 | [CA2000： 超出范围前释放对象](../code-quality/ca2000-dispose-objects-before-losing-scope.md) | 由于可能发生异常事件，导致对象的终结器无法运行，因此，应显式释放对象，以避免对该对象的所有引用超出范围。 |
| CA2001 | [CA2001:避免调用有问题的方法](../code-quality/ca2001-avoid-calling-problematic-methods.md) | 某个成员调用可能存在危险或有问题的方法。 |
| CA2002 |[CA2002:不要锁定具有弱标识的对象](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md) |当可以跨应用程序域边界直接进行访问对象时，则认为该对象具有弱标识。 对于尝试获取对具有弱标识的对象的锁的线程，该线程可能会被其他应用程序域中持有对同一对象的锁的另一线程所阻止。 |
| CA2003 |[CA2003:不要将纤程视为线程](../code-quality/ca2003-do-not-treat-fibers-as-threads.md) | 托管线程被视为 [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] 线程。 |
| CA2004 | [CA2004:移除对 GC 的调用。保持连接](../code-quality/ca2004-remove-calls-to-gc-keepalive.md) | 如果转换为使用 SafeHandle，请移除所有对 GC.KeepAlive (object) 的调用。 在这种情况下，类不必调用 GC.KeepAlive。 这将假定它们没有终结器，而只是依赖 SafeHandle 来为它们完成 OS 句柄。 |
| CA2006 | [CA2006:使用 SafeHandle 封装本机资源](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md) | 在托管代码中使用 IntPtr 可能意味着潜在的安全性和可靠性方面的问题。 必须检查所有使用 IntPtr 之处，以确定是否需要在该处使用 SafeHandle 或类似的技术。 |
| CA2007 | [CA2007:不直接等待任务](ca2007-do-not-directly-await-task.md) | 异步方法[等待](/dotnet/csharp/language-reference/keywords/await)<xref:System.Threading.Tasks.Task>直接。 当异步方法等待<xref:System.Threading.Tasks.Task>延续直接创建了任务的同一线程中发生。 此行为可以极大地降低性能，并且可能会导致在 UI 线程上发生死锁。 请考虑调用<xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType>以指示您的继续符的意图。 |
| CA2100 | [CA2100:检查存在安全漏洞的 SQL 查询](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md) | 一个方法使用按该方法的字符串参数生成的字符串设置 System.Data.IDbCommand.CommandText 属性。 此规则假定字符串参数中包含用户输入。 基于用户输入生成的 SQL 命令字符串易于受到 SQL 注入式攻击。 |
| CA2101 |[CA2101:指定对 P/Invoke 字符串自变量封送处理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md) | 某平台调用成员允许部分受信任的调用方，具有一个字符串参数，并且不显式封送该字符串。 这可能导致潜在的安全漏洞。 |
| CA2102 | [CA2102:在常规处理程序中捕捉非 CLSCompliant 异常](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md) | 程序集中未用 RuntimeCompatibilityAttribute 标记或用 RuntimeCompatibility(WrapNonExceptionThrows = false) 标记的某个成员包含一个处理 System.Exception 的 catch 块，而不包含紧跟其后的一般 catch 块。 |
| CA2103 | [CA2103:检查命令性安全](../code-quality/ca2103-review-imperative-security.md) |某个方法使用命令性安全，并且可能正在使用在要求处于活动状态时可以更改的状态信息或返回值来构造权限。 应尽可能使用声明性安全。 |
| CA2104 |[CA2104:不要声明只读可变引用类型](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md) | 外部可见类型包含外部可见的只读字段，该字段为可变的引用类型。 可变类型是实例数据可被修改的类型。 |
| CA2105 | [CA2105:不应仅读取数组字段](../code-quality/ca2105-array-fields-should-not-be-read-only.md) |向包含数组的字段应用 readonly（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 ReadOnly）修饰符时，无法将该字段更改为引用其他数组。 但是，可以更改在只读字段中存储的数组的元素。 |
| CA2106 | [CA2106:安全断言](../code-quality/ca2106-secure-asserts.md) | 某个方法断言权限，但不对调用方执行任何安全检查。 如果在不执行任何安全检查的情况下断言安全权限，则会在代码中留下可利用的安全漏洞。 |
| CA2107 | [CA2107:检查 deny 权限和允许仅使用情况](../code-quality/ca2107-review-deny-and-permit-only-usage.md) |PermitOnly 方法和 CodeAccessPermission.Deny 安全操作应仅由具有.NET Framework 安全性的高级的知识的用户使用。 应当对使用这些安全操作的代码进行安全检查。 |
| CA2108 | [CA2108:检查有关值类型的声明性安全](../code-quality/ca2108-review-declarative-security-on-value-types.md) | 公共或受保护值类型受数据访问或链接要求保护。 |
| CA2109 | [CA2109:检查可见的事件处理程序](../code-quality/ca2109-review-visible-event-handlers.md) | 检测到公共事件处理方法或受保护事件处理方法。 除非绝对必要，否则不应公开事件处理方法。 |
| CA2111 |[CA2111:指针不应是可见](../code-quality/ca2111-pointers-should-not-be-visible.md) | 指针不是私有、内部或只读指针。 恶意代码可以更改指针的值，这样就有可能访问内存中的任意位置或导致应用程序或系统故障。 |
| CA2112 | [CA2112:受保护的类型不应公开字段](../code-quality/ca2112-secured-types-should-not-expose-fields.md) | 一个公共或受保护类型包含公共字段，并受链接要求保护。 如果代码可以访问受链接要求保护的类型的实例，则该代码不必满足此链接要求就可以访问该类型的字段。 |
| CA2114 | [CA2114:方法安全性应是类型的超集](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md) | 一个方法不应同时有同一操作的方法级别和类型级别的声明性安全。 |
| CA2115 | [CA2115:调用 GC。使用本机资源时保持连接](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md) | 该规则检测由于在非托管代码仍在使用非托管资源时终止该非托管资源而可能发生的错误。 |
| CA2116 | [CA2116:APTCA 方法应只调用 APTCA 方法](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md) |当完全受信任的程序集上存在 APTCA (AllowPartiallyTrustedCallersAttribute) 时，如果该程序集执行另一个不允许部分受信任调用方的程序集中的代码，则可能会产生安全漏洞。 |
| CA2117 | [CA2117:APTCA 类型应只扩展 APTCA 基类型](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md) | 当完全受信任的程序集上存在 APTCA 时，如果程序集中的某个类型是从不允许部分受信任调用方的类型继承而来，则可能会产生安全漏洞。 |
| CA2118 | [CA2118:检查 SuppressUnmanagedCodeSecurityAttribute 用法](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) |SuppressUnmanagedCodeSecurityAttribute 为执行使用 COM 互操作或操作系统调用的非托管代码的成员更改默认的安全系统行为。 此特性主要用于提高性能；不过，提高性能的同时会显著增加安全风险。 |
| CA2119 | [CA2119:密封满足私有接口的方法](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md) | 可继承的公共类型为内部（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 Friend）接口提供可重写的方法实现。 若要修复与此规则的冲突，请禁止方法在程序集外重写。 |
| CA2120 | [CA2120:安全的序列化构造函数](../code-quality/ca2120-secure-serialization-constructors.md) | 此类型的构造函数采用了 System.Runtime.Serialization.SerializationInfo 对象和 System.Runtime.Serialization.StreamingContext 对象（序列化构造函数的签名）。 此构造函数不受安全检查的保护，但类型中的一个或多个常规构造函数受保护。 |
| CA2121 | [CA2121:静态构造函数应为私有](../code-quality/ca2121-static-constructors-should-be-private.md) | 系统在创建第一个类型实例或引用任何静态成员之前调用静态构造函数。 如果静态构造函数不是私有，则系统以外的代码可以调用它。 根据构造函数中执行的操作，这可能导致意外行为。 |
| CA2122 | [CA2122:不要间接公开方法使用链接请求](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md) | 公共或受保护成员具有链接要求，且由不执行任何安全检查的成员调用。 链接请求仅检查直接调用方的权限。 |
| CA2123 | [CA2123:重写链接请求应与基相同](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md) | 该规则将一个方法与其基方法（该基方法为另一个类型中的接口或虚方法）相匹配，然后比较两者的链接请求。 如果与此规则冲突，则恶意调用方只需调用不安全的方法，即可跳过该链接要求。 |
| CA2124 | [CA2124:Try 包装易受攻击的 finally 子句在外部](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md) | 公共或受保护方法中含有 try/finally 块。 finally 块似乎要重置安全状态，并且自身不包括在某个 finally 块中。 |
| CA2126 | [CA2126:类型链接请求需要继承请求](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md) | 一个公共的非密封类型受链接要求保护，并且具有可重写的方法。 类型和方法都不受继承要求保护。 |
| CA2127 | [CA2136:成员不应具有冲突的透明度注释](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md) | 在 100%透明的程序集不能出现关键代码。 此规则分析在类型、 字段和方法级别任何 SecurityCritical 批注的 100%透明程序集。 |
| CA2128 |[CA2147:透明方法不得使用安全断言](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md) | 此规则分析的所有方法和程序集是 100%透明或混合透明/关键，并标记 Assert 的任何声明性或命令性用法中的类型。 |
| CA2129 | [CA2140:透明代码不得引用安全关键项](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md) | 用 SecurityTransparentAttribute 标记的方法调用标为 SecurityCritical 的非公共成员。 此规则分析混合透明/关键的程序集中的所有方法和类型，并标记透明代码中对未标为 SecurityTreatAsSafe 的非公共关键代码的任何调用。 |
| CA2130 | [CA2130:安全关键常量应是透明的](../code-quality/ca2130-security-critical-constants-should-be-transparent.md) | 未对常数值实施透明强制，因为编译器内联常数值以便在运行时不需要查找。 常数字段应为安全透明的，以便代码评审阅者不会假定透明代码不能访问常数。 |
| CA2131 | [CA2131:安全关键类型不能参与类型等效性](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md) | 某个类型参与了类型等效，该类型本身或该类型的成员或字段用 SecurityCriticalAttribute 特性标记。 对于任何关键的类型或包含参与类型等效的关键方法或字段的类型，将引发此规则。 当 CLR 检测到这样的类型时，在运行时将不会加载它并引发 TypeLoadException。 通常，仅在用户手动实现类型等效而不是通过依赖 tlbimp 和编译器进行类型等效时，才会引发此规则。 |
| CA2132 | [CA2132:默认构造函数必须至少与基类型默认构造函数一样关键](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md) |具有 SecurityCriticalAttribute 的类型和成员无法供 Silverlight 应用程序代码使用。 安全关键类型和成员只能供 .NET Framework for Silverlight 类库中的受信任代码使用。 因为派生类中的某个公共或受保护构造必须有与其基类相同或更大的透明度，所以不能从标记为 SecurityCritical 类中派生应用程序中的类。 |
| CA2133 | [CA2133:委托必须绑定到方法，具有一致的透明度](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md) | 将对一个具有以下特点的方法引发此警告：该方法将用 SecurityCriticalAttribute 标记的委托绑定到一个透明的或用 SecuritySafeCriticalAttribute 标记的方法。 还会对另一个具有以下特点的方法引发此警告：该方法将透明的或安全关键的委托绑定到一个关键方法。 |
| CA2134 | [CA2134:重写基方法时，方法必须保持一致的透明度](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md) |当用 SecurityCriticalAttribute 标记的方法重写一个透明的或用 SecuritySafeCriticalAttribute 标记的方法时，将会引发此规则。 当一个透明的或用 SecuritySafeCriticalAttribute 标记的方法重写一个用 SecurityCriticalAttribute 标记的方法时，也会引发此规则。 该规则在重写虚方法或实现接口时应用。 |
| CA2135 | [CA2135:级别 2 程序集不应包含 Linkdemand](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md) | 在级别为 2 的安全规则集中已弃用 LinkDemand。 现在使用 SecurityCriticalAttribute 特性标记方法、类型和字段，而不是使用 LinkDemand 在实时 (JIT) 编译时进行强制安全检查。 |
| CA2136 | [CA2136:成员不应具有冲突的透明度注释](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md) | 将透明特性从较大作用域的代码元素应用到较小作用域的元素。 具有较大作用域的代码元素的透明特性优于第一个元素中包含的代码元素的透明特性。 例如，用 SecurityCriticalAttribute 特性标记的类不能包含用 SecuritySafeCriticalAttribute 特性标记的方法。 |
| CA2137 | [CA2137:透明方法必须仅包含可验证 IL](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md) | 某个方法包含无法验证的代码或通过引用返回类型。 在尝试通过安全透明代码执行无法验证的 Microsoft 中间语言 (MSIL) 时将引发此规则。 但是，此规则不包含完整的 IL 验证程序，而是使用试探法来捕捉 MSIL 验证的大部分冲突。 |
| CA2138 | [CA2138:透明方法不得调用具有 SuppressUnmanagedCodeSecurity 特性的方法](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md) | 一个安全透明方法调用使用 SuppressUnmanagedCodeSecurityAttribute 特性标记的方法。 |
| CA2139 | [CA2139:透明方法不能使用 HandleProcessCorruptingExceptions 特性](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md) | 任何透明的并尝试通过使用 HandleProcessCorruptedStateExceptionsAttribute 特性处理进程损坏异常的方法将会引发此规则。 进程损坏异常属于异常的 CLR 版本 4.0 异常分类，如 AccessViolationException。 HandleProcessCorruptedStateExceptionsAttribute 特性只由安全关键方法使用，并且如果应用于透明的方法，则将被忽略。 |
| CA2140 | [CA2140:透明代码不得引用安全关键项](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md) | 用 SecurityCriticalAttribute 特性标记的代码元素是安全关键的。 透明方法不能使用安全关键元素。 如果透明类型尝试使用安全关键类型，则会引发 TypeAccessException、MethodAccessException 或 FieldAccessException。 |
| CA2141 |[CA2141：透明方法不得满足 LinkDemand](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md) | 安全透明方法调用未用 APTCA 特性标记的程序集中的方法，或者安全透明方法满足某个类型或方法的 LinkDemand。 |
| CA2142 | [CA2142:不应使用 Linkdemand 保护透明代码](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md) | 对于需要 LinkDemand 来访问它们的透明方法，将会引发此规则。 安全透明代码不应负责验证某个操作的安全，因此不应要求权限。 |
| CA2143 | [CA2143:透明方法不应使用安全要求](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md) | 安全透明代码不应负责验证某个操作的安全，因此不应要求权限。 安全透明代码应使用完整的需求来作出安全决策并且安全关键代码不应依赖透明代码以进行完全的请求。 |
| CA2144 | [CA2144:透明代码不应从字节数组加载程序集](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md) | 透明代码安全检查不像关键代码的安全检查一样全面，因为透明代码不能执行安全敏感的操作。 从字节数组中加载的程序集在透明代码中可能不会被注意到，并且该字节数组可能包含确实需要审核的关键或更重要的安全关键代码。 |
| CA2145 | [CA2145:不应使用 SuppressUnmanagedCodeSecurityAttribute 修饰透明方法](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md) | 用 SuppressUnmanagedCodeSecurityAttribute 特性修饰的方法有一个隐式的 LinkDemand 作用于调用它的任何方法。 此 LinkDemand 要求调用代码是关键安全的。 用 SecurityCriticalAttribute 特性标记使用 SuppressUnmanagedCodeSecurity 的方法会使此需求对方法的调用方更加明显。 |
| CA2146 | [CA2146:类型必须至少与其基类型和接口一样关键](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md) | 当派生类型具有的安全透明特性与其基类型或实现的接口不是同样关键时，将引发此规则。 只有关键类型可以从关键基类型派生或实现关键接口，并且只有关键或关键安全类型可以从安全关键基类型派生或实现关键安全接口。 |
| CA2147 |[CA2147:透明方法不得使用安全断言](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md) | 标记为 SecurityTransparentAttribute 的代码未被授予足够的权限进行断言。 |
| CA2149 | [CA2149:透明方法不得调入本机代码](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md) | 对于直接调用到本机代码中（例如通过使用 P/Invoke）的任何透明方法，将引发此规则。 违反此规则会导致级别 2 透明度模型中的 MethodAccessException，以及级别 1 透明度模型中对 UnmanagedCode 的完全要求。 |
| CA2151 |[CA2151:具有关键类型的字段应是安全关键](../code-quality/ca2151-fields-with-critical-types-should-be-security-critical.md) | 若要使用安全关键类型，引用该类型的代码必须是安全关键或安全可靠关键。 即使引用是间接的，也需如此。 因此，具有安全透明字段或安全可靠关键字段具有误导性，因为透明代码仍然无法访问该字段。 |
| CA2200 | [CA2200:再次引发以保留堆栈详细信息](../code-quality/ca2200-rethrow-to-preserve-stack-details.md) | 再次引发某个异常，在 throw 语句中显式指定了该异常。 如果通过在 throw 语句中指定异常来重新引发该异常，则引发该异常的原始方法与当前方法之间的方法调用的列表将丢失。 |
| CA2201 | [CA2201:不要引发保留的异常类型](../code-quality/ca2201-do-not-raise-reserved-exception-types.md) | 这使得很难检测和调试原始错误。 |
| CA2202 | [CA2202:多次未释放对象](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md) |某个方法实现所包含的代码路径可能导致对同一对象多次调用 System.IDisposable.Dispose 或与 Dispose 等效的方法（例如，用于某些类型的 Close() 方法）。 |
| CA2204 | [CA2204:应正确拼写文本](../code-quality/ca2204-literals-should-be-spelled-correctly.md) | 方法体中的文本字符串包含一个或多个未被 Microsoft 拼写检查器库识别的单词。 |
| CA2205 | [CA2205:使用 Win32 API 的托管等效项](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md) | 操作系统调用方法的定义，并且具有等效功能的方法位于.NET Framework 类库。 |
| CA2207 | [CA2207:值类型的静态字段以内联方式初始化](../code-quality/ca2207-initialize-value-type-static-fields-inline.md) | 某值类型声明了显式静态构造函数。 要修复与该规则的冲突，请在声明它时初始化所有静态数据并移除静态构造函数。 |
| CA2208 |[CA2208:正确实例化参数异常](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md) | 调用了异常类型 ArgumentException 或其派生类型的默认（无参数）构造函数，或者向异常类型 ArgumentException 或其派生类型的参数化构造函数传递了错误的字符串参数。 |
| CA2210 |[CA2210:程序集应具有有效的强名称](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md) | 强名称可避免客户端在不知情的情况下加载已被篡改的程序集。 除非极为有限的几种情况，否则不应部署没有强名称的程序集。 如果共享或发布未正确签名的程序集，则该程序集可能被篡改，公共语言运行时可能不会加载该程序集；而用户可能必须在他/她的计算机上禁用验证。 |
| CA2211 |[CA2211： 非常量非常量字段不应是可见](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md) | 不是常数也不是只读字段的静态字段不是线程安全的。 必须严格控制对这类字段的访问，并需要高级编程技术来同步对类对象的访问。 |
| CA2212 | [CA2212:未标记使用 WebMethod 服务的组件](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md) |继承自 System.EnterpriseServices.ServicedComponent 的类型中的方法标记有 System.Web.Services.WebMethodAttribute。 因为 WebMethodAttribute 和 ServicedComponent 方法在上下文和事务流方面的行为和需求有冲突，所以该方法的行为在某些情况下会不正确。 |
| CA2213 | [CA2213：应释放可释放的字段](../code-quality/ca2213-disposable-fields-should-be-disposed.md) | 实现 System.IDisposable 的类型声明了同样实现 IDisposable 的类型的字段。 字段的 Dispose 方法不由声明类型的 Dispose 方法调用。 |
| CA2214 | [CA2214:不要在构造函数中调用可重写方法](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md) | 构造函数调用虚方法时，可能尚未执行调用该方法的实例的构造函数。 |
| CA2215 | [CA2215:方法应调用基类 dispose](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md) | 如果类型继承自可释放类型，则必须从它自己的 Dispose 方法中调用基类型的 Dispose 方法。 |
| CA2216 |[CA2216:可释放类型应声明终结器](../code-quality/ca2216-disposable-types-should-declare-finalizer.md) | 实现 System.IDisposable 并包含建议使用非托管资源的字段的类型未实现 Object.Finalize 所描述的终结器。 |
| CA2217 | [CA2217:不使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md) |外部可见的枚举使用 FlagsAttribute 标记，并且它包含的一个或多个值不是 2 的幂或不是为该枚举定义的其他值的组合。 |
| CA2218 |[CA2218:重写 Equals 时重写 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md) | GetHashCode 基于当前实例返回一个适合哈希算法和哈希表之类的数据结构的值。 两个相等的同类型对象必须返回相同的哈希代码。 |
| CA2219 | [CA2219:不会引发异常子句中的异常](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md) | 如果在 finally 或 fault 子句中引发异常，新异常将隐藏活动异常。 当在 filter 子句中引发异常时，运行时会在不提示的情况下捕捉异常。 这使得很难检测和调试原始错误。 |
| CA2220 | [CA2220:终结器应调用基类的终结器](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md) | 终止必须通过继承层次结构传播。 为确保这一点，类型必须从其自身的 Finalize 方法调用它们的基类 Finalize 方法。 |
| CA2221 |[CA2221:终结器应受到保护](../code-quality/ca2221-finalizers-should-be-protected.md) | 终结器必须使用族访问修饰符。 |
| CA2222 | [CA2222:不要递减继承的成员的可见性](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md) |不能更改所继承成员的访问修饰符。 将继承的成员更改为私有成员不能防止调用方访问该方法的基类实现。 |
| CA2223 | [CA2223:成员不应由多个返回类型不同](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md) | 虽然公共语言运行时允许使用返回类型区分其余部分都相同的成员，但该功能不包含在公共语言规范中，也不是各种 .NET 编程语言的共同功能。 |
| CA2224 | [CA2224:重写 equals 方法重载相等运算符](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md) | 某公共类型实现了等号运算符，但是没有重写 Object.Equals。 |
| CA2225 | [CA2225:运算符重载具有命名的备用项](../code-quality/ca2225-operator-overloads-have-named-alternates.md) |检测到运算符重载，但未找到预期的指定备用方法。 命名的备用成员提供了对与运算符相同的功能的访问，它提供给开发人员，在用不支持重载运算符的语言进行编程时使用。 |
| CA2226 | [CA2226:运算符应有对称重载](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md) | 某个类型实现了相等运算符或不等运算符，却未实现相反运算符。 |
| CA2227 |[CA2227:集合属性应为只读](../code-quality/ca2227-collection-properties-should-be-read-only.md) |使用可写的集合属性，用户可以将该集合替换为不同的集合。 只读属性禁止替换该集合，但仍允许设置单个成员。 |
| CA2228 | [CA2228:不要发行未发布的资源格式](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md) | 通过使用预发布版本的.NET Framework 生成的资源文件可能不是可由支持的.NET Framework 版本。 |
| CA2229 | [CA2229：实现序列化构造函数](../code-quality/ca2229-implement-serialization-constructors.md) | 要修复与该规则的冲突，请实现序列化构造函数。 对于密封类，请使构造函数成为私有；否则，请使构造函数成为受保护。 |
| CA2230 | [CA2230:自变量使用 params](../code-quality/ca2230-use-params-for-variable-arguments.md) | 公共或受保护类型包含一个使用 VarArgs 调用约定（而不是 params 关键字）的公共或受保护方法。 |
| CA2231 | [CA2231：重写 ValueType.Equals 时应重载相等运算符](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md) | 值类型重写 Object.Equals，但未实现相等运算符。 |
| CA2232 | [CA2232:使用 STAThread 标记 Windows 窗体的入口点](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md) | STAThreadAttribute 指示应用程序的 COM 线程模型是单线程单元。 使用 Windows 窗体的任何应用程序的入口点上必须存在此特性；如果没有此特性，则 Windows 组件可能无法正常工作。 |
| CA2233 |[CA2233:运算不应溢出](../code-quality/ca2233-operations-should-not-overflow.md) | 如果未首先验证操作数，则不应执行算术运算。 这将确保运算结果不会超出所涉及数据类型的允许值范围。 |
| CA2234 | [CA2234:传递 System.Uri 对象，而不是字符串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md) | 调用了带有一个字符串参数的方法，该参数的名称中包含“uri”、“URI”、“urn”、“URN”、“url”或“URL”。 此方法的声明类型包含具有 System.Uri 参数的对应方法重载。 |
| CA2235 | [CA2235：标记所有不可序列化的字段](../code-quality/ca2235-mark-all-non-serializable-fields.md) | 在可以序列化的类型中声明了类型不可序列化的实例字段。 |
| CA2236 | [CA2236:对 ISerializable 类型调用基类方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md) | 若要修复与该规则的冲突，请从相应的派生类型方法或构造函数调用基类型 GetObjectData 方法或序列化构造函数。 |
| CA2237 | [CA2237：用 SerializableAttribute 标记 ISerializable 类型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) | 若要被公共语言运行时识别为可序列化，类型必须用 SerializableAttribute 特性标记，即使该类型通过实现 ISerializable 接口使用了自定义的序列化例程也是如此。 |
| CA2238 |[CA2238:正确实现序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md) | 处理序列化事件的方法的签名、返回类型或可见性不正确。 |
| CA2239 | [CA2239:提供反序列化方法为可选字段](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md) | 某个类型有一个使用 System.Runtime.Serialization.OptionalFieldAttribute 特性标记的字段，并且该类型没有提供反序列化事件处理方法。 |
| CA2240 | [CA2240:正确实现 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md) | 若要修复与该规则的冲突，请使 GetObjectData 方法可见且可以重写，并确保所有实例字段都包括在序列化进程中，或者使用 NonSerializedAttribute 特性显式标记所有实例字段。 |
| CA2241 | [CA2241:提供正确的自变量为格式化方法](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md) | 传递给 System.String.Format 的 format 自变量不包含对应于每个对象自变量的格式项，反之亦然。 |
| CA2242 |[CA2242:正确测试 NaN](../code-quality/ca2242-test-for-nan-correctly.md) | 此表达式对照 Single.Nan 或 Double.Nan 测试某个值。 使用 Single.IsNan(Single) 或 Double.IsNan(Double) 测试该值。 |
| CA2243 |[CA2243:应正确分析特性字符串文本](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md) | 特性的字符串文本参数不能正确解析为 URL、GUID 或版本。 |
| CA5122 | [CA5122 P/Invoke 声明不应为安全临界](../code-quality/ca5122-p-invoke-declarations-should-not-be-safe-critical.md) | 当方法执行安全敏感性操作时，将被标记为 SecuritySafeCritical，但透明代码使用它们也是安全的。 透明代码决不能通过通过 P/Invoke 直接调用本机代码。 因此，将 P/Invoke 标记为安全关键将使透明代码无法调用它，并且会误导安全分析。 |