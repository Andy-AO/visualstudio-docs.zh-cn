---
title: 如何：创建 LINQ to SQL 类 （O-R 设计器） 之间的关联 （关系） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6971da256d638b8248e49235a4d8d3ded71dc10e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056765"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>如何：创建 LINQ to SQL 类 （O/R 设计器） 之间的关联 （关系）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 中实体类之间的关联类似于数据库中表之间的关系。 可以使用“关联编辑器”对话框创建实体类之间的关联。  
  
 使用“关联编辑器”对话框创建关联时，必须选择父类和子类。 父类是包含主键的实体类；子类是包含外键的实体类。 例如，如果创建映射到 Northwind Customers 和 Orders 表的实体类，则 Customer 类将是父类，而 Order 类将是子类。  
  
> [!NOTE]
>  当您将从表**服务器资源管理器**/**数据库资源管理器**拖动到[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)]([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)])，自动创建基于现有关联在数据库中的外键关系。  
  
 在 O/R 设计器中选择该关联时创建关联后，就会中的某些可配置属性**属性**窗口。 （关联是用相关类之间的连线表示的。）下表提供对关联的属性的说明。  
  
|属性|描述|  
|--------------|-----------------|  
|**基数**|控制关联是一对多关系还是一对一关系。|  
|**子属性**|指定是否在父类上创建一个属性，作为关联关系外键一方上的子记录的集合或对这些子记录的引用。 例如，在客户与订单之间的关联如果**子属性**设置为**True**的父类上创建名为 Orders 的属性。|  
|**父属性**|子类上引用关联父类的属性。 例如，在 Customer 和 Order 之间的关联中，在 Order 类上创建一个名为 Customer 的属性，用来引用与订单关联的客户。|  
|**参与的属性**|显示关联属性，并提供一个省略号按钮 (...)，该按钮可重新打开“关联编辑器”对话框。|  
|**唯一**|指定外目标列是否具有唯一性约束。|  
  
### <a name="to-create-an-association-between-entity-classes"></a>创建实体类之间的关联  
  
1. 右击表示关联中的父类的实体类，指向“添加”，然后单击“关联”。  
  
2. 验证在“关联编辑器”对话框中是否选择了正确的“父类”。  
  
3. 选择组合框中的“子类”。  
  
4. 选择实现类之间的关联的“关联属性”。 通常，这种关联对应于数据库中定义的外键关系。 例如，在 Customers 和 Orders 关联中，**关联属性**是为每个类的 CustomerID。  
  
5. 单击“确定”创建关联。  
  
## <a name="see-also"></a>请参阅  
 [LINQ to SQL 工具在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [演练：创建 LINQ to SQL 类 （O-R 设计器）](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [DataContext 方法 （O/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)   
 [如何：表示主键](http://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)
