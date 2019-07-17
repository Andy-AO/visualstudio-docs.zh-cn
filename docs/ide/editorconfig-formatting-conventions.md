---
title: EditorConfig 适用的 .NET 格式设置约定
ms.date: 06/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3218e819d8f94cf760cdc75d6bfa6d29d0a29568
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823339"
---
# <a name="formatting-conventions"></a>格式设置约定

Visual Studio 的 EditorConfig 适用的格式设置约定划分为两个类别：

- [.NET 格式设置](#net-formatting-settings)

- [C# 格式设置](#c-formatting-settings)

## <a name="rule-format"></a>规则格式

格式设置约定的规则具有以下格式：

`rule_name = value`

对于许多规则，可为 `value` 指定 `true`（以此样式为首选项）或 `false`（不以此样式为首选项）。 对于其他规则，可指定值（如 `flush_left` 或 `before_and_after`）来说明在什么时间以及在什么位置应用此规则。 不需要指定严重性。

## <a name="net-formatting-settings"></a>.NET 格式设置

本节中的格式设置规则均适用于 C# 和 Visual Basic 代码。

- [组织 using](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>组织 using 指令

这些格式设置规则与 `using` 指令和 `Imports` 语句的排序和显示有关。

.editorconfig 文件示例  ：

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnetsortsystemdirectivesfirst"></a>dotnet\_sort\_system\_directives_first

|||
|-|-|
| **规则名称** | dotnet_sort_system_directives_first |
| **适用的语言** | C# 和 Visual Basic |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 按字母顺序对 System.* `using` 指令排序并将其置于其他 using 指令前面。<br /><br />`false` - 不将 System.* `using` 指令置于其他 `using` 指令前面。 |
| **Visual Studio 默认值** | `true` |

代码示例：

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

#### <a name="dotnetseparateimportdirectivegroups"></a>dotnet\_separate\_import\_directive\_groups

|||
|-|-|
| **规则名称** | dotnet_separate_import_directive_groups |
| **适用的语言** | C# 和 Visual Basic |
| **引入的版本** | Visual Studio 2017 版本 15.5 |
| **值** | `true` - 在 `using` 指令组之间放置一个空白行。<br /><br />`false` - 不在 `using` 指令组之间放置空白行。 |
| **Visual Studio 默认值** | `false` |

代码示例：

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-settings"></a>C# 格式设置

本节中的格式设置规则仅适用于 C# 代码。

- [换行符选项](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [缩进选项](#indentation-options)
  - csharp_indent_case_contents
  - csharp_indent_switch_labels
  - csharp_indent_labels
- [间距选项](#spacing-options)
  - csharp_space_after_cast
  - csharp_space_after_keywords_in_control_flow_statements
  - csharp_space_between_method_declaration_parameter_list_parentheses
  - csharp_space_between_method_call_parameter_list_parentheses
  - csharp_space_between_parentheses
  - csharp_space_before_colon_in_inheritance_clause
  - csharp_space_after_colon_in_inheritance_clause
  - csharp_space_around_binary_operators
  - csharp_space_between_method_declaration_empty_parameter_list_parentheses
  - csharp_space_between_method_call_name_and_opening_parenthesis
  - csharp_space_between_method_call_empty_parameter_list_parentheses
  - csharp_space_after_comma
  - csharp_space_after_dot
- [换行选项](#wrap-options)
  - csharp_preserve_single_line_statements
  - csharp_preserve_single_line_blocks

### <a name="new-line-options"></a>换行选项

这些格式设置规则与是否使用新行设置代码的格式有关。

.editorconfig 文件示例  ：

```ini
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="csharpnewlinebeforeopenbrace"></a>csharp\_new\_line\_before\_open_brace

此规则与左大括号 `{` 应放在前面代码的同一行还是新行上有关。 对于此规则，指定“全部”、“无”或一个或多个码位元素，如方法或属性，从而定义此规则的应用时间     。 若要指定多个代码元素，请使用逗号 (,) 分隔。

|||
|-|-|
| **规则名称** | csharp_new_line_before_open_brace |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `all` - 对于所有表达式，需要将大括号置于新行（“Allman”样式）。<br /><br />`none` - 对于所有表达式，需要将大括号置于同一行（“K&R”）。<br /><br />`accessors`、`anonymous_methods`、`anonymous_types`、`control_blocks`、`events`、`indexers`、`lambdas`、`local_functions`、`methods`、`object_collection_array_initializers`、`properties`、`types` - 对于指定的代码元素，需要将大括号置于新行（“Allman”样式）。 |
| **Visual Studio 默认值** | `all` |

代码示例：

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="csharpnewlinebeforeelse"></a>csharp\_new\_line\_before_else

|||
|-|-|
| **规则名称** | csharp_new_line_before_else |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 将 `else` 语句置于新行。<br /><br />`false` - 将 `else` 语句置于同一行。 |
| **Visual Studio 默认值** | `true` |

代码示例：

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="csharpnewlinebeforecatch"></a>csharp\_new\_line\_before_catch

|||
|-|-|
| **规则名称** | csharp_new_line_before_catch |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 将 `catch` 语句置于新行。<br /><br />`false` - 将 `catch` 语句置于同一行。 |
| **Visual Studio 默认值** | `true` |

代码示例：

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="csharpnewlinebeforefinally"></a>csharp\_new\_line\_before_finally

|||
|-|-|
| **规则名称** | csharp_new_line_before_finally |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 需要将 `finally` 语句置于右大括号后的新行。<br /><br />`false` - 需要将 `finally` 语句置于右大括号所在的同一行。 |
| **Visual Studio 默认值** | `true` |

代码示例：

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="csharpnewlinebeforemembersinobjectinitializers"></a>csharp\_new\_line\_before\_members\_in\_object_initializers

|||
|-|-|
| **规则名称** | csharp_new_line_before_members_in_object_initializers |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 需要将对象初始值设定项的成员置于单独的行<br /><br />`false` - 需要将对象初始值设定项的成员置于同一行 |
| **Visual Studio 默认值** | `true` |

代码示例：

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="csharpnewlinebeforemembersinanonymoustypes"></a>csharp\_new\_line\_before\_members\_in\_anonymous_types

|||
|-|-|
| **规则名称** | csharp_new_line_before_members_in_anonymous_types |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 需要将匿名类型的成员置于单独的行<br /><br />`false` - 需要将匿名类型的成员置于同一行 |
| **Visual Studio 默认值** | `true` |

代码示例：

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="csharpnewlinebetweenqueryexpressionclauses"></a>csharp_new_line_between_query_expression_clauses

|||
|-|-|
| **规则名称** | csharp_new_line_between_query_expression_clauses |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 要求将查询表达式子句的元素置于单独的行<br /><br />`false` - 要求将查询表达式子句的元素置于同一行 |
| **Visual Studio 默认值** | `true` |

代码示例：

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a>缩进选项

这些格式设置规则与是否使用缩进设置代码的格式有关。

.editorconfig 文件示例  ：

```ini
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="csharpindentcasecontents"></a>csharp\_indent\_case_contents

|||
|-|-|
| **规则名称** | csharp_indent_case_contents |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 缩进 `switch` case 内容<br /><br />`false` - 不缩进 `switch` case 内容 |
| **Visual Studio 默认值** | `true` |

- 如果此规则设置为“true”，则为 i。 
- 如果此规则设置为“false”，则为 d。 

代码示例：

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharpindentswitchlabels"></a>csharp\_indent\_switch_labels

|||
|-|-|
| **规则名称** | csharp_indent_switch_labels |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 缩进 `switch` 标签<br /><br />`false` - 不缩进 `switch` 标签 |
| **Visual Studio 默认值** | `true` |

代码示例：

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharpindentlabels"></a>csharp\_indent_labels

|||
|-|-|
| **规则名称** | csharp_indent_labels |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `flush_left` - 标签置于最左侧的列<br /><br />`one_less_than_current` - 将标签置于比当前上下文少一个缩进的位置<br /><br />`no_change` - 将标签置于与当前上下文相同的缩进位置 |
| **Visual Studio 默认值** | `no_change` |

代码示例：

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

### <a name="spacing-options"></a>间距选项

这些格式设置规则与是否使用空格字符设置代码的格式有关。

.editorconfig 文件示例  ：

```ini
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_after_comma = true
csharp_space_after_dot = false
```

#### <a name="csharpspaceaftercast"></a>csharp\_space\_after_cast

|||
|-|-|
| **规则名称** | csharp_space_after_cast |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 转换和值之间需要空格<br /><br />`false` - 转换和值之间无需空格  |
| **Visual Studio 默认值** | `false` |

代码示例：

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharpspaceafterkeywordsincontrolflowstatements"></a>csharp_space_after_keywords_in_control_flow_statements

|||
|-|-|
| **规则名称** | csharp_space_after_keywords_in_control_flow_statements |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 在 `for` 循环等控制流语句中，关键字后需要空格<br /><br />`false` - 在 `for` 循环等控制流语句中，关键字后不需要空格  |
| **Visual Studio 默认值** | `true` |

代码示例：

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharpspacebetweenmethoddeclarationparameterlistparentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|||
|-|-|
| **规则名称** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 在方法声明参数列表的左括号之后和右括号之前放置空格字符<br /><br />`false` - 不要在方法声明参数列表的左括号之后和右括号之前放置空格字符 |
| **Visual Studio 默认值** | `false` |

代码示例：

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharpspacebetweenmethodcallparameterlistparentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|||
|-|-|
| **规则名称** | csharp_space_between_method_call_parameter_list_parentheses |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 在方法调用的左括号之后和右括号之前放置空格字符<br /><br />`false` - 不要在方法调用的左括号之后和右括号之前放置空格字符 |
| **Visual Studio 默认值** | `false` |

代码示例：

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharpspacebetweenparentheses"></a>csharp_space_between_parentheses

|||
|-|-|
| **规则名称** | csharp_space_between_parentheses |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `control_flow_statements` - 在控制流语句的括号之间放置空格<br /><br />`expressions` - 在表达式的括号之间放置空格<br /><br />`type_casts` - 在类型转换中的括号之间放置空格 |
| **Visual Studio 默认值** | `false` |

如果省略此规则或使用 `control_flow_statements`、`expressions` 或 `type_casts` 以外的值，则不会应用该设置。

代码示例：

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharpspacebeforecolonininheritanceclause"></a>csharp\_space\_before\_colon\_in\_inheritance_clause

|||
|-|-|
| **规则名称** | csharp_space_before_colon_in_inheritance_clause |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 15.7 版 |
| **值** | `true` - 类型声明中的基或接口的冒号前需要空格<br /><br />`false` - 类型声明中的基或接口的冒号前不需要空格  |
| **Visual Studio 默认值** | `true` |

代码示例：

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### <a name="csharpspaceaftercolonininheritanceclause"></a>csharp\_space\_after\_colon\_in\_inheritance_clause

|||
|-|-|
| **规则名称** | csharp_space_after_colon_in_inheritance_clause |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 15.7 版 |
| **值** | `true` - 类型声明中的基或接口的冒号后需要空格<br /><br />`false` - 类型声明中的基或接口的冒号后不需要空格  |
| **Visual Studio 默认值** | `true` |

代码示例：

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### <a name="csharpspacearoundbinaryoperators"></a>csharp\_space\_around\_binary_operators

|||
|-|-|
| **规则名称** | csharp_space_around_binary_operators |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 15.7 版 |
| **值** | `before_and_after` - 在二元运算符前后插入空格<br /><br />`none` - 删除二元运算符前后的空格<br /><br />`ignore` - 忽略二元运算符前后的空格 |
| **Visual Studio 默认值** | `before_and_after` |

如果省略此规则或使用 `before_and_after`、`none` 或 `ignore` 以外的值，则不会应用该设置。

代码示例：

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharpspacebetweenmethoddeclarationemptyparameterlistparentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|||
|-|-|
| **规则名称** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 15.7 版 |
| **值** | `true` - 在方法声明的空参数列表括号内插入空格<br /><br />`false` - 删除方法声明的空参数列表括号内的空格 |
| **Visual Studio 默认值** | `false` |

代码示例：

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharpspacebetweenmethodcallnameandopeningparenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|||
|-|-|
| **规则名称** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 15.7 版 |
| **值** | `true` - 在方法调用名称和左括号之间插入空格<br /><br />`false` - 删除方法调用名称和左括号之间的空格 |
| **Visual Studio 默认值** | `false` |

代码示例：

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharpspacebetweenmethodcallemptyparameterlistparentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|||
|-|-|
| **规则名称** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 15.7 版 |
| **值** | `true` - 在空参数列表的括号中插入空格<br /><br />`false` - 删除空参数列表括号内的空格 |
| **Visual Studio 默认值** | `false` |

代码示例：

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharpspaceaftercomma"></a>csharp_space_after_comma

|||
|-|-|
| **规则名称** | csharp_space_after_comma |
| **适用的语言** | C# |
| **值** | `true` - 在逗号后面插入空格<br /><br />`false` - 删除逗号后面的空格 |
| **Visual Studio 默认值** | `true` |

代码示例：

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharpspaceafterdot"></a>csharp_space_after_dot

|||
|-|-|
| **规则名称** | csharp_space_after_dot |
| **适用的语言** | C# |
| **值** | `true` - 在点号后面插入空格<br /><br />`false` - 删除点号后面的空格 |
| **Visual Studio 默认值** | `false` |

代码示例：

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

### <a name="wrap-options"></a>换行选项

这些格式设置规则与语句和代码块中单一行以及单独的行的使用有关。

.editorconfig 文件示例  ：

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharppreservesinglelinestatements"></a>csharp_preserve_single_line_statements

|||
|-|-|
| **规则名称** | csharp_preserve_single_line_statements |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 将语句和成员声明保留在同一行上<br /><br />`false` - 将语句和成员声明保留在不同行上 |
| **Visual Studio 默认值** | `true` |

代码示例：

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharppreservesinglelineblocks"></a>csharp_preserve_single_line_blocks

|||
|-|-|
| **规则名称** | csharp_preserve_single_line_blocks |
| **适用的语言** | C# |
| **引入的版本** | Visual Studio 2017 版本 15.3 |
| **值** | `true` - 将代码块保留在单个行上<br /><br />`false` - 将代码块保留在单独的行上 |
| **Visual Studio 默认值** | `true` |

代码示例：

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

## <a name="see-also"></a>请参阅

- [语言约定](editorconfig-language-conventions.md)
- [命名约定](editorconfig-naming-conventions.md)
- [EditorConfig 的 .NET 编码约定设置](editorconfig-code-style-settings-reference.md)
