---
title: 如何：手动创建 Web 模板 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4bf604e747158c651f284c6463c2c2f65ae3c47a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651806"
---
# <a name="how-to-manually-create-web-templates"></a>如何：手动创建 Web 模板
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

创建 Web 模板与创建其他种类的模板不同。 由于 Web 项目模板出现在 " **添加新** 网站" 对话框中，并且 web 项目项由编程语言分类，因此 .vstemplate 文件必须将模板指定为 Web 模板，并识别编程语言。

> [!NOTE]
> Web 模板必须包含空 webproj 文件，该文件通过使用元素 `Project` 的属性 `File` 指定。 虽然 Web 项目不需要项目文件，但需要此文件来让 Web 模板正常运行。

### <a name="to-manually-create-a-web-template"></a>手动创建 Web 模板

1. 创建 Web 项目。

2. 修改或删除项目中的文件，或将新文件添加到项目。

3. 创建 XML 文件，并用 vstemplate 文件扩展名将其保存在与项目相同的目录中。 不要将其添加到 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的项目中。

4. 创建 vstemplate XML 文件以提供项目模板元数据。 有关详细信息，请参阅下一节的示例。

5. 查找 vstemplate 文件中的 `ProjectType` 元素，将文本值设置为 `Web`。

6. 在该 `ProjectType` 元素之后，添加 `ProjectSubType` 元素并将文本值设置为模板的编程语言。 编程语言可以是下列值之一：

   - CSharp

   - VisualBasic

     例如：

   ```
   <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
   </TemplateData>
   ```

7. 选择模板中的文件（包括 vstemplate 文件），右键单击所选文件，单击“发送至”，然后单击“压缩的文件夹（zip 格式）”********。 这些文件被压缩到一个 .zip 文件中。

8. 将该 .zip 模板文件放入 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 项目模板目录。 默认情况下，该目录为 \My Documents\Visual Studio Version\My Exported Templates\\**。

## <a name="example"></a>示例
 以下示例显示 Web 项目模板的基本 vstemplate 文件。

```
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>另请参阅
 [创建项目和项模板](../ide/creating-project-and-item-templates.md) [Visual Studio 模板架构引用](../extensibility/visual-studio-template-schema-reference.md)
