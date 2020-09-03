---
title: 使用事务保存数据 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85f3584073523e748168faf569aa918ba912fbf8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652838"
---
# <a name="save-data-by-using-a-transaction"></a>使用事务保存数据
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用命名空间将数据保存在事务中 <xref:System.Transactions> 。 使用 <xref:System.Transactions.TransactionScope> 对象参与自动管理的事务。

 项目不是使用对 System.web 程序集的引用创建的，因此，您需要手动添加对使用事务的项目的引用。

> [!NOTE]
> <xref:System.Transactions>Windows 2000 或更高版本支持命名空间。

 实现事务的最简单方法是 <xref:System.Transactions.TransactionScope> 在语句中实例化对象 `using` 。 有关详细信息，请参阅 [Using 语句](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1)和 [using 语句](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3) (。 ) 语句中运行的代码 `using` 参与事务。

 若要提交事务，请调用 <xref:System.Transactions.TransactionScope.Complete%2A> 方法，作为 using 块中的最后一条语句。

 若要回滚事务，请在调用方法之前引发异常 <xref:System.Transactions.TransactionScope.Complete%2A> 。

 有关详细信息，请参阅 [在事务中保存数据](../data-tools/save-data-in-a-transaction.md)。

### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>添加对 System.web dll 的引用

1. 在“项目”菜单中，选择“添加引用”。********

2. 在 " **.net** " 选项卡上 (SQL Server) 项目 **SQL Server** "选项卡，选择" **系统**"，然后选择 **" 确定 "**。

     对 System.Transactions.dll 的引用将添加到项目。

### <a name="to-save-data-in-a-transaction"></a>在事务中保存数据

- 添加代码以在包含事务的 using 语句中保存数据。 下面的代码演示如何 <xref:System.Transactions.TransactionScope> 在 using 语句中创建并实例化对象：

     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]

## <a name="see-also"></a>另请参阅
 [将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)
