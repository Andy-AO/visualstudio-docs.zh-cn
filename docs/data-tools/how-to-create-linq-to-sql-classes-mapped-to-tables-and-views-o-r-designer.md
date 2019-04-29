---
title: 如何：创建映射到表和视图的 LINQ to SQL 类（O-R 设计器）
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1b9fb62fe3b6d92c617fc89f083aadcd262579e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567004"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>如何：创建映射到表和视图的 LINQ to SQL 类（O/R 设计器）

映射到数据库表和视图的 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 类称为“实体类”。 实体类映射到记录，而一个实体类的各个属性则映射到构成一条记录的各个列。 创建通过拖动表或视图从基于数据库表或视图的实体类**服务器资源管理器**或**数据库资源管理器**拖动到[Visual Studio中的LINQtoSQL工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md). **O/R 设计器**生成的类并应用特定[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]属性来启用[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]功能 (数据通信和编辑功能<xref:System.Data.Linq.DataContext>)。 有关详细信息[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]类，请参阅[LINQ to SQL 对象模型](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)。

> [!NOTE]
> **O/R 设计器**是一个简单的对象关系映射器，因为它仅支持 1:1 映射关系。 换句话说，实体类与数据库表或视图之间只能具有 1:1 映射关系。 不支持复杂映射（例如，将一个实体类映射到多个表）。 但是，可以将一个实体类映射到一个联接多个相关表的视图。

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>创建映射到数据库表或视图的 LINQ to SQL 类

通过将表或视图从**服务器资源管理器**或**数据库资源管理器**拖到**O/R 设计器**创建实体类除了<xref:System.Data.Linq.DataContext>方法，用于执行更新。

默认情况下，[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 运行时创建用于将更改从可更新的实体类保存回数据库的逻辑。 此逻辑基于表的架构（列定义和主键信息）。 如果不需要此行为，则可以配置实体类以使用存储过程执行插入、更新和删除，而不是使用默认的 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 运行时行为。 有关详细信息，请参阅[如何：分配存储过程以便执行更新、插入和删除操作（O/R 设计器）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>创建映射到数据库表或视图的 LINQ to SQL 类

1. 在“服务器”或“数据库资源管理器”中，展开“表”或“视图”，并找到要在应用程序中使用的数据库表或视图。

2. 将表或视图拖动到**O/R 设计器**。

     一个实体类将创建并显示在设计图面上。 该实体类的属性映射到所选表或视图中的列。

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>创建对象数据源并在窗体中显示数据

使用创建实体类后**O/R 设计器**，可以创建对象数据源并填充[数据源窗口](add-new-data-sources.md#data-sources-window)与实体类。

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>创建基于 LINQ to SQL 实体类的对象数据源

1. 在“生成”菜单中，单击“生成解决方案”以生成项目。

2. 若要打开**数据源**窗口，然后在**数据**菜单中，单击**显示数据源**。

3. 在 **“数据源”** 窗口中，单击 **“添加新数据源”**。

4. 单击“选择数据源类型”页上的“对象”，然后单击“下一步”。

5. 展开节点，然后找到并选择您的类。

    > [!NOTE]
    > 如果“Customer”类不可用，则退出向导，生成项目，然后重新运行向导。

6. 单击“完成”以创建数据源，并将“Customer”实体类添加到“数据源”窗口。

7. 将项从“数据源”窗口拖动到窗体。

## <a name="see-also"></a>请参阅

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [演练：创建 LINQ to SQL 类（O-R 设计器）](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [DataContext 方法（O/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)
- [如何：创建映射到存储过程和函数的 DataContext 方法（O/R 设计器）](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL 对象模型](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [演练：自定义实体类的插入、更新和删除行为](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [如何：创建 LINQ to SQL 类之间的关联（关系）（O/R 设计器）](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)