---
title: 在管理员门户中编辑订阅 | Microsoft 文档
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: conceptual
description: 了解管理员如何编辑订阅分配。
ms.openlocfilehash: 7245facbaf966593160bc44dc15bc2fd71622347
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783479"
---
# <a name="editing-visual-studio-subscription-assignments"></a>编辑 Visual Studio 订阅分配

作为订阅管理员，可以更改分配给组织内个人的订阅。  本文讨论可以进行更改的类型并提供必要的步骤。

## <a name="making-changes-to-subscriber-information"></a>对订阅者的信息进行更改
可以编辑订阅者的信息来更正错误或更新信息。

若要对订阅者进行编辑，请在鼠标悬停在订阅者的电子邮件地址旁时，选择出现的省略号 (…)。 此时将显示下拉列表。  选择“编辑”  ，以修改订阅者的详细信息。 也可双击网格中订阅者的行来打开编辑窗口。
> [!div class="mx-imgBorder"]
> ![选择要对其进行编辑的订阅者](_img/edit-license/select-subscriber.png)

可以更新订阅者的名字、姓氏、国籍、语言和下载。 编辑订阅者的信息，然后单击“保存”  。

   > [!NOTE]
   > 如果需要更改订阅者的订阅级别，则需要从门户中删除该用户，然后再重新添加。 订阅级别不可编辑。

## <a name="editing-multiple-subscribers-using-bulk-edit"></a>使用批量编辑对多个订阅者进行编辑

可使用批量编辑进程一次编辑多个订阅者。 此功能主要用于正在更改公司电子邮件地址的组织，或者决定对下载进行限制的组织。

   > [!IMPORTANT]
   > 订阅级别（即 Enterprise、Professional 等）和订阅 GUID 无法更改。  如果尝试上传这些更改项，上传将失败。

1. 若要一次编辑多个订阅者，请导航到“订阅者”选项卡。在顶部功能区中，单击“批量编辑”  。

2. 批量编辑使用 Excel 模板编辑订阅者信息。 在“批量编辑”框中，单击“导出此 excel”，以下载当前包含其所有信息的订阅者列表  。
   > [!div class="mx-imgBorder"]
   > ![编辑许可证 - 导出批量编辑列表](_img/edit-license/edit-license-bulk-edit-export.png)

3. 接下来，将文件保存到本地，以便能够轻松找到该文件，并在上传之前对其进行必要的更改。 为确保上传成功，请勿编辑订阅级别或订阅 GUID，否则会导致上传失败  。

4. 返回到 Visual Studio 订阅管理门户，在“批量编辑”对话框中，单击“浏览”  。 选择之前保存的 Excel 文件，然后单击“确定”  。 屏幕上随即显示上传进度。
   > [!div class="mx-imgBorder"]
   > ![编辑许可证 - 批量编辑文件上传](_img/edit-license/edit-license-bulk-file-upload1.png)

5. 文件上传后，将看到上传成功的通知。 此时，编辑将反映到订阅者信息当中。
