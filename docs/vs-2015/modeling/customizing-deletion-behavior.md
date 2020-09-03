---
title: 自定义删除行为 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords:
- Domain-Specific Language, deletion
ms.assetid: c6bf088d-52c6-4817-af45-ddae745bb5a9
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d0dcfc5724e87d57d2803b9b64a6eb121314b99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655049"
---
# <a name="customizing-deletion-behavior"></a>自定义删除行为
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

删除一个元素通常会导致同时删除相关的元素。 将删除连接到该元素的所有关系以及任何子元素。 此行为称为 *删除传播*。 可以自定义删除传播，例如安排删除其他相关元素。 通过编写程序代码，可以根据模型的状态删除传播。 还可能发生其他更改以响应删除。

 本主题包含下列部分：

- [默认删除行为](#default)

- [设置角色的“传播删除”选项](#property)

- [重写删除闭包](#closure) –使用此方法，删除可能会导致删除相邻元素。

- [使用 OnDeleting 和 OnDeleted](#ondeleting) –使用这些方法，其中的响应可能包括其他操作，例如更新存储内部或外部的值。

- [删除规则](#rules) -使用规则传播应用商店中任何类型的更新，其中一项更改可能会导致其他更改。

- [删除事件](#rules) –使用存储事件将更新传播到存储区之外，例如，传播到其他 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 文档。

- "[取消合并" –使用](#unmerge)"取消合并" 操作撤消将子元素附加到其父级的合并操作。

## <a name="default-deletion-behavior"></a><a name="default"></a> 默认删除行为
 默认情况下，以下规则控制删除传播：

- 如果删除某个元素，也将删除所有嵌入元素。 嵌入元素是作为嵌入关系的目标的元素，而此元素是嵌入关系的源。 例如，如果有一个从 **唱片集** 到 **歌曲**的嵌入关系，则在删除特定相册时，还将删除其所有歌曲。

     相反，删除 Song 并不会删除 Album。

- 默认情况下，删除不会沿着引用关系传播。 如果从**唱片集**到**艺术家**的引用关系**ArtistPlaysOnAlbum** ，则删除唱片集不会删除任何相关艺术家，并且删除艺术家不会删除任何唱片集。

     但是，删除将沿着一些内置关系传播。 例如，当删除模型元素时，还将删除它在关系图上的形状。 元素和形状通过 `PresentationViewsSubject` 引用关系相关联。

- 不管是在源角色上还是在目标角色上，都将删除连接到该元素的每个关系。 对方角色的元素的角色属性不再包含删除的元素。

## <a name="setting-the-propagate-delete-option-of-a-role"></a><a name="property"></a> 设置角色的 "传播删除" 选项
 可以使删除沿着引用关系传播，或从嵌入子级传播到其父级。

#### <a name="to-set-delete-propagation"></a>设置删除传播

1. 在 DSL 定义关系图上，选择要将传播删除到的 *角色* 。 该角色由域关系框的左侧或右侧的线表示。

    例如，如果想要指定在删除 Album 时，也将删除相关的 Artist，则选择已连接到域类 Artist 的角色。

2. 在属性窗口中，设置 " **传播删除** " 属性。

3. 按 F5 并验证：

   - 当删除此关系的实例时，也将删除选定角色的元素。

   - 当删除对方角色的元素时，将删除此关系的实例，也将删除此角色的相关元素。

   还可以在 " **DSL 详细信息**" 窗口中查看 "**传播删除**" 选项。 选择域类，然后在 "DSL 详细信息" 窗口中，通过单击窗口一侧的按钮打开 " **删除行为** " 页。 为每个关系的相反角色显示 " **传播** " 选项。 " **删除样式** " 列指示 " **传播** " 选项是否为其默认设置，但不会有任何不同的效果。

## <a name="delete-propagation-by-using-program-code"></a>通过使用程序代码删除传播
 DSL 定义文件中的选项仅允许你选择是否将删除传播到邻近内容。 若要实现删除传播的更复杂方案，你可以编写程序代码。

> [!NOTE]
> 若要将程序代码添加到 DSL 定义，请在 **dsl** 项目中创建一个单独的代码文件，并写入部分定义以增加生成的代码文件夹中的类。 有关详细信息，请参阅 [编写代码以定制域特定语言](../modeling/writing-code-to-customise-a-domain-specific-language.md)。

## <a name="defining-a-delete-closure"></a><a name="closure"></a> 定义删除关闭
 如果给定了初始选择，则删除操作将使用 _YourModel_**DeleteClosure** 类来确定要删除的元素。 它将重复调用 `ShouldVisitRelationship()` 和 `ShouldVisitRolePlayer()`，从而遍历这些关系图。 可以重写这些方法。 ShouldVisitRolePlayer 与链接的标识和一个链接角色的元素一起提供。 它应返回以下值之一：

- **VisitorFilterResult**-应删除元素，然后查看者应继续尝试元素的其他链接。

- **VisitorFilterResult** -不应删除元素，除非另一个查询回复应删除它。

- **VisitorFilterResult** –即使另一个查询回答 **"是"**，并且遍历者不应尝试该元素的其他链接，也不能删除该元素。

```
// When a musician is deleted, delete their albums with a low rating.
// Override methods in <YourDsl>DeleteClosure in DomainModel.cs
partial class MusicLibDeleteClosure
{
  public override VisitorFilterResult ShouldVisitRolePlayer
    (ElementWalker walker, ModelElement sourceElement, ElementLink elementLink,
    DomainRoleInfo targetDomainRole, ModelElement targetRolePlayer)
  {
    ArtistAppearsInAlbum link = elementLink as ArtistAppearsInAlbum;
    if (link != null
       && targetDomainRole.RolePlayer.Id == Album.DomainClassId)
    {
      // Count other unvisited links to the Album of this link.
      if (ArtistAppearsInAlbum.GetLinksToArtists(link.Album)
              .Where(linkAlbumArtist =>
                     linkAlbumArtist != link &&
                     !walker.Visited(linkAlbumArtist))
              .Count() == 0)
      {
        // Should delete this role player:
        return VisitorFilterResult.Yes;
      }
      else
        // Don’t delete unless another relationship deletes it:
        return VisitorFilterResult.DoNotCare;
    }
    else
    {
      // Test for and respond to other relationships and roles here.

      // Not the relationship or role we’re interested in.
      return base.ShouldVisitRolePlayer(walker, sourceElement,
             elementLink, targetDomainRole, targetRolePlayer);
    }
  }
}

```

 闭包技术可确保在开始删除之前确定要删除的元素和链接集。 查看器还将闭包的结果和来自模型其他部分的结果组合在一起。

 但是，该技术假设删除在关系图中仅影响其邻近内容：无法使用此方法删除模型的另一部分中的元素。 如果想要添加元素或进行其他更改以响应删除，则不能使用此技术。

## <a name="using-ondeleting-and-ondeleted"></a><a name="ondeleting"></a> 使用 OnDeleting 和 OnDeleted
 可以在域类或域关系中重写 `OnDeleting()` 或 `OnDeleted()`。

1. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> 当要删除某个元素，但在断开其关系之前，将调用。 该元素仍可在其他元素中来回导航，并且仍位于 `store.ElementDirectory` 中。

    如果同时删除多个元素，则在执行删除操作前为所有元素调用 OnDeleting。

    `IsDeleting` 为 true。

2. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> 在元素已删除时调用。 它将保留在 CLR 堆中，以便在需要时可执行“撤消”，但它已与其他元素取消链接并已从 `store.ElementDirectory` 中删除。 对于关系，角色仍引用旧角色扮演者。`IsDeleted` 的值为 true 时才有效。

3. 当用户在创建元素后调用“撤消”时，以及在“重做”中重复以前的删除时，将调用 OnDeleting 和 OnDeleted。 使用 `this.Store.InUndoRedoOrRollback` 来避免在这些情况下更新存储元素。 有关详细信息，请参阅 [如何：使用事务更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)。

   例如，以下代码将在删除 Album 的最后一个子级 Song 时删除该 Album：

```

// Delete the parent Album when the last Song is deleted.
// Override methods in the embedding relationship between Album and Song:
partial class AlbumHasSongs
{
  protected override void OnDeleted()
  {
    base.OnDeleted();
    // Don't perform in-store actions in undo:
    if (this.Store.InUndoRedoOrRollback) return;
    // Relationship source and target still work:
    // Don't bother if source is already on its way out:
    if (!this.Album.IsDeleting && !this.Album.IsDeleted)
    {
      if (this.Album.Songs.Count == 0)
      {
        this.Album.Delete();
} } } }

```

 从关系的删除触发通常比从角色元素触发更有用，因为这将同时在删除元素和删除关系本身时起作用。 但是，对于引用关系，你可能想要在删除相关元素时而不是在删除关系本身时传播删除。 此示例将在删除 Album 的最后一个参与的 Artist 时删除该 Album，但它不会在删除关系时响应：

```
using System.Linq; ...
// Assumes a many-many reference relationship
// between Artist and Album.
partial class Artist
{
  protected override void OnDeleting()
  {
    base.OnDeleting();
    if (this.Store.InUndoRedoOrRollback) return;
    List<Album> toDelete = new List<Album>();
    foreach (Album album in this.Albums)
    {
      if (album.Artists.Where(artist => !artist.IsDeleting)
                        .Count() == 0)
      {
        toDelete.Add(album);
      }
    }
    foreach (Album album in toDelete)
    {
      album.Delete();
} } }

```

 当在元素上执行 <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> 时，将调用 OnDeleting 和 OnDeleted。 这些方法始终内联执行 – 即在实际删除前后立即执行。 如果代码将删除两个或多个元素，则将在所有元素上按顺序交替调用 OnDeleting 和 OnDeleted。

## <a name="deletion-rules-and-events"></a><a name="rules"></a> 删除规则和事件
 作为 OnDelete 处理程序的替代方法，你可以定义删除规则和删除事件。

1. **删除** 和 **删除** 规则仅在事务中触发，而不是在撤消或重做操作。 可以设置它们以进行排队，从而在执行删除的事务末尾执行它们。 Deleting 规则始终在队列中的任何 Deleted 规则之前执行。

     使用规则来传播仅影响存储中的元素的更改，包括关系、关系图元素及其属性。 通常，Deleting 规则用于传播删除，而 Delete 规则用于创建替换元素和关系。

     有关详细信息，请参阅 [规则在模型内部传播更改](../modeling/rules-propagate-changes-within-the-model.md)。

2. **删除** 的存储事件将在事务结束时调用，并在撤消或重做后调用。 因此，它可以用于将删除传播到存储外的对象，例如文件、数据库项或 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中的其他对象。

     有关详细信息，请参阅 [事件处理程序在模型外部传播更改](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

    > [!WARNING]
    > 已删除某个元素后，可以访问其域属性值，但无法导航关系链接。 但是，如果在关系上设置了 Deleted 事件，则还可以访问作为其角色扮演者的两个元素。 因此，如果想要响应模型元素的删除，但不想要访问它链接到的元素，则在关系上而不是模型元素的域类上设置 Delete 事件。

### <a name="example-deletion-rules"></a>示例 Deletion 规则

```
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]
internal class AlbumDeletingRule : DeletingRule
{
  public override void ElementDeleting(ElementDeletingEventArgs e)
  {
    base.ElementDeleting(e);
    // ...perform tasks to propagate imminent deletion
  }
}
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]
internal class AlbumDeletedRule : DeleteRule
{
  public override void ElementDeleted(ElementDeletedEventArgs e)
  {
    base.ElementDeleted(e);
    // ...perform tasks such as creating new elements
  }
}

// The rule must be registered:
public partial class MusicLibDomainModel
{
  protected override Type[] GetCustomDomainModelTypes()
  {
    List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
    types.Add(typeof(AlbumDeletingRule));
    types.Add(typeof(AlbumDeletedRule));
    // If you add more rules, list them here.
    return types.ToArray();
  }
}

```

### <a name="example-deleted-event"></a>示例 Deleted 事件

```
partial class NestedShapesSampleDocData
{
  protected override void OnDocumentLoaded(EventArgs e)
  {
    base.OnDocumentLoaded(e);
    DomainRelationshipInfo commentRelationship =
          this.Store.DomainDataDirectory
          .FindDomainRelationship(typeof(CommentsReferenceComponents));

    this.Store.EventManagerDirectory.ElementDeleted.Add(commentRelationship,
      new EventHandler<ElementDeletedEventArgs>(CommentLinkDeleted));
  }

  private void CommentLinkDeleted (object sender, ElementDeletedEventArgs e)
  {
    CommentsReferenceComponents link = e.ModelElement as CommentsReferenceComponents;
    Comment comment = link.Comment;
    Component component = link.Subject;
    if (comment.IsDeleted)
    {
      // The link was deleted because the comment was deleted.
      System.Windows.Forms.MessageBox.Show("Removed comment on " + component.Name);
    }
    else
    {
      // It was just the link that was deleted - the comment itself remains.
      System.Windows.Forms.MessageBox.Show("Removed comment link to "
           + component.Name);
    }
  }
}

```

## <a name="unmerge"></a><a name="unmerge"></a> 取消合并
 将子元素附加到其父级的操作称为 *merge*。 当从工具箱创建新元素或元素组时、从模型的另一个部分进行移动时，或从剪贴板进行复制时，将会发生此情况。 除了在父级和其新子级之间创建嵌入关系，合并操作还可以设置其他关系、创建辅助元素以及设置元素中的属性值。 合并操作封装在元素合并指令 (EMD) 中。

 EMD 还封装了互补的取消 *合并* 或 `MergeDisconnect` 操作。 如果你具有已通过使用合并构造的元素的群集，则建议使用关联的取消合并将元素从该群集中移除（如果想要使剩余元素保留在一致的状态下）。 通常，取消合并操作将使用前面部分中所述的技术。

 有关详细信息，请参阅 [自定义元素创建和移动](../modeling/customizing-element-creation-and-movement.md)。

## <a name="see-also"></a>另请参阅
 [自定义复制行为](../modeling/customizing-copy-behavior.md)[自定义元素创建和移动](../modeling/customizing-element-creation-and-movement.md)[编写代码以自定义域特定语言](../modeling/writing-code-to-customise-a-domain-specific-language.md)
