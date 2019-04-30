---
title: 文本模板实用工具方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0da69de4a91ebabce4af99e26195b349ef5daa60
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411413"
---
# <a name="text-template-utility-methods"></a>文本模板实用工具方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

有几种方法，始终都可供您编写代码时[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]文本模板。 这些方法中定义<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。  
  
> [!TIP]
> 此外可以使用其他方法和常规 （而不是预处理） 文本模板中的主机环境提供服务。 例如，可以解析文件路径、 记录错误，并获取所提供的服务[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]和任何已加载的程序包。  有关详细信息，请参阅[从文本模板访问 Visual Studio](http://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4)。  
  
## <a name="write-methods"></a>编写方法  
 可以使用`Write()`和`WriteLine()`方法要追加的标准代码块，而不是使用表达式的代码块中的文本。 下面的两个代码块在功能上等效。  
  
##### <a name="code-block-with-an-expression-block"></a>将表达式块的代码块  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### <a name="code-block-using-writeline"></a>代码块使用 WriteLine()  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 您可能会发现有必要使用这些实用程序方法之一而不是嵌套的控件结构与冗长的代码块将表达式块。  
  
 `Write()`并`WriteLine()`方法有两个重载，另一个采用单个字符串参数，另一个使用复合格式字符串以及要在字符串中包含的对象的数组 (如`Console.WriteLine()`方法)。 下面的两个使用`WriteLine()`在功能上等效：  
  
```  
<#  
    string msg = "Say: {0}, {1}, {2}";  
    string s1 = "hello";  
    string s2 = "goodbye";  
    string s3 = "farewell";  
  
    WriteLine(msg, s1, s2, s3);  
    WriteLine("Say: hello, goodbye, farewell");  
#>   
```  
  
## <a name="indentation-methods"></a>缩进方法  
 可以使用缩进方法来设置文本模板的输出格式。 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>类具有`CurrentIndent`字符串显示当前缩进文本模板中的属性和一个`indentLengths`字段，它是一组已添加缩进。 您可以添加使用缩进`PushIndent()`方法和减法使用缩进`PopIndent()`方法。 如果你想要删除所有的缩进，则使用`ClearIndent()`方法。 下面的代码块显示使用这些方法：  
  
```  
<#  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    ClearIndent();  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
#>  
```  
  
 此代码块生成以下输出：  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## <a name="error-and-warning-methods"></a>错误和警告方法  
 可以使用错误和警告实用程序方法添加到消息[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]错误列表。 例如，下面的代码会将一条错误消息添加到错误列表。  
  
```  
<#  
  try  
  {  
    string str = null;  
    Write(str.Length.ToString());  
  }  
  catch (Exception e)  
  {  
    Error(e.Message);  
  }  
#>    
```  
  
## <a name="access-to-host-and-service-provider"></a>对主机和服务提供程序的访问  
 该属性`this.Host`可以提供对属性执行模板主机公开的访问。 若要使用`this.Host`，则必须设置`hostspecific`属性中`<@template#>`指令：  
  
 `<#@template ... hostspecific="true" #>`  
  
 类型`this.Host`取决于主机执行该模板的类型。 在运行中的模板[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，可以强制转换`this.Host`到`IServiceProvider`才能访问服务，如 IDE。 例如：  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## <a name="using-a-different-set-of-utility-methods"></a>使用一组不同的实用工具方法  
 作为文本生成过程的一部分，你的模板文件转换为一个类，这始终命名为`GeneratedTextTransformation`继承<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。 如果你想要使用不同设置的方法而不是，您可以编写您自己的类，并在模板指令中指定。 您的类必须继承<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 使用`assembly`指令引用程序集可以在其中找到编译的类。
