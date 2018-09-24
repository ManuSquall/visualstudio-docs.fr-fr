---
title: Personnalisation du comportement de la commande de suppression
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords:
- Domain-Specific Language, deletion
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5bc8ecdbbbed1d7d128a5102141c7130dcaef026
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775773"
---
# <a name="customizing-deletion-behavior"></a>Personnalisation du comportement de la commande de suppression
La suppression d'un élément provoque généralement aussi la suppression des éléments associés. Toutes les relations qui y sont connectées et tous les éléments enfants sont supprimés. Ce comportement se nomme *suppression de la propagation*. Vous pouvez personnaliser la propagation de la suppression, par exemple pour que des éléments associés supplémentaires soient supprimés. En écrivant du code de programme, vous pouvez faire en sorte que la propagation de la suppression dépende de l'état du modèle. Vous pouvez aussi provoquer d'autres modifications en réponse à une suppression.

 Cette rubrique comporte les sections suivantes :

-   [Comportement de suppression par défaut](#default)

-   [Définition de l’option de propagation de la suppression d’un rôle](#property)

-   [Substitution de la fermeture de suppression](#closure) -Utilisez cette technique où suppression peut provoquer la suppression des éléments voisins.

-   [Utilisation de OnDeleting et OnDeleted](#ondeleting) -utiliser ces méthodes où la réponse pourrait inclure d’autres actions telles que la mise à jour une valeur à l’intérieur ou en dehors du magasin.

-   [Règles de suppression](#rules) -utiliser des règles pour propager des mises à jour de tout type dans le magasin, où il peut entraîner une modification à d’autres personnes.

-   [Événements de suppression](#rules) -événements de magasin d’utilisation pour propager des mises à jour en dehors du magasin, par exemple vers d’autres [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] documents.

-   [UnMerge](#unmerge) -utilisez l’opération UnMerge pour annuler l’opération de fusion qui attaché un élément enfant à son parent.

##  <a name="default"></a> Comportement de suppression par défaut
 Par défaut, les règles suivantes régissent la propagation de la suppression :

-   Si un élément est supprimé, tous les éléments incorporés sont également supprimés. Les éléments incorporés sont ceux qui sont les cibles de relations d'incorporation pour lesquelles cet élément est la source. Par exemple, s’il existe une relation d’incorporation de **Album** à **chanson**, lorsqu’un Album spécifique est supprimé, tous ses morceaux est également supprimées.

     En revanche, la suppression d'un morceau ne supprime pas l'album.

-   Par défaut, la suppression ne se propage pas le long des relations de référence. S’il existe une relation de référence **ArtistPlaysOnAlbum** de **Album** à **artiste**, suppression d’un album ne supprime pas les artistes associés et suppression d’un artiste n’est pas supprime aucun album.

     Toutefois, la suppression se propage le long de certaines relations intégrées. Par exemple, quand un élément de modèle est supprimé, sa forme sur le diagramme est également supprimée. L'élément et la forme sont liés par la relation de référence `PresentationViewsSubject`.

-   Chaque relation qui est connectée à l'élément, au rôle source ou cible, est supprimée. La propriété de rôle de l'élément au niveau du rôle opposé ne contient plus l'élément supprimé.

##  <a name="property"></a> Définition de l’option de propagation de la suppression d’un rôle
 Vous pouvez faire en sorte que la suppression soit propagée le long d'une relation de référence ou d'un enfant incorporé vers son parent.

#### <a name="to-set-delete-propagation"></a>Pour définir la propagation de suppression

1.  Sur le diagramme de définition DSL, sélectionnez le *rôle* à laquelle vous souhaitez que la propagation à supprimer. Le rôle est représenté par la ligne qui se trouve à gauche ou à droite d'une zone de relation de domaine.

     Par exemple, si vous voulez spécifier qu'à chaque fois qu'un album est supprimé les artistes associés doivent également être supprimés, vous devez sélectionner le rôle connecté à la classe de domaine Artiste.

2.  Dans la fenêtre Propriétés, définissez la **Propagates Delete** propriété.

3.  Appuyez sur F5 et vérifiez que :

    -   Quand une instance de cette relation est supprimée, l'élément au rôle sélectionné sera également supprimé.

    -   Quand un élément au rôle opposé est supprimé, les instances de cette relation seront supprimées et les éléments associés à ce rôle seront supprimés.

 Vous pouvez également voir le **Propagates Delete** option dans le **détails DSL** fenêtre. Sélectionnez une classe de domaine et, dans la fenêtre Détails DSL, ouvrez le **supprimer un comportement** page en cliquant sur le bouton situé sur le côté de la fenêtre. Le **propager** option est affichée pour le rôle opposé de chaque relation. Le **supprimer le Style** colonne indique si le **propager** option se trouve à sa valeur par défaut, mais il n’a aucun effet distinct.

## <a name="delete-propagation-by-using-program-code"></a>Propagation de la suppression à l'aide de code de programme
 Les options dans le fichier de définition DSL vous permettent uniquement de choisir si la suppression se propage à un voisin immédiat. Pour implémenter un modèle plus complexe de propagation de la suppression, vous pouvez écrire du code de programme.

> [!NOTE]
>  Pour ajouter du code de programme à votre définition DSL, créez un fichier de code séparé dans le **Dsl** de projet et écrivez des définitions partielles pour augmenter les classes dans le dossier Code généré. Pour plus d’informations, consultez [écriture du Code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md).

##  <a name="closure"></a> Définition d’une fermeture de suppression
 L’opération de suppression utilise la classe _Votre_modèle_**DeleteClosure** pour déterminer les éléments à supprimer, étant donné une sélection initiale. Elle appelle `ShouldVisitRelationship()` et `ShouldVisitRolePlayer()` de manière répétée, en parcourant le graphique des relations. Vous pouvez substituer ces méthodes. L'identité d'un lien et l'élément à l'un des rôles du lien sont fournis à la méthode ShouldVisitRolePlayer. Elle doit retourner l'une des valeurs suivantes :

-   **VisitorFilterResult.Yes**: l’élément doit être supprimé et que l’analyseur doit continuer à essayer les de l’élément autres liens.

-   **VisitorFilterResult.DoNotCare** -l’élément ne doit pas être supprimé, sauf si une autre requête répond qu’il doit être supprimé.

-   **VisitorFilterResult.Never** -l’élément ne doit pas être supprimé, même si une autre requête répond **Oui**, et l’analyseur ne doit pas essayer les de l’élément autres liens.

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
        // Don't delete unless another relationship deletes it:
        return VisitorFilterResult.DoNotCare;
    }
    else
    {
      // Test for and respond to other relationships and roles here.

      // Not the relationship or role we're interested in.
      return base.ShouldVisitRolePlayer(walker, sourceElement,
             elementLink, targetDomainRole, targetRolePlayer);
    }
  }
}

```

 La technique de fermeture garantit que le jeu d'éléments et de lien à supprimer est déterminé avant que la suppression ne commence. L'analyseur combine aussi les résultats de votre fermeture avec ceux d'autres parties du modèle.

 Toutefois, cette technique part du principe que la suppression affecte uniquement ses voisins dans le graphique des relations : vous ne pouvez pas appliquer cette méthode pour supprimer un élément dans une autre partie du modèle. Vous ne pouvez pas l'appliquer si vous souhaitez ajouter des éléments ou apporter d'autres modifications en réponse à une suppression.

##  <a name="ondeleting"></a> Utilisation de OnDeleting et OnDeleted
 Vous pouvez substituer `OnDeleting()` ou `OnDeleted()` dans une classe de domaine ou dans une relation de domaine.

1.  La méthode <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> est appelée quand un élément est sur le point d'être supprimé, mais avant que ses relations aient été déconnectées. Il est encore accessible à partir d'autres éléments et se trouve toujours dans `store.ElementDirectory`.

     Si plusieurs éléments sont supprimés en même temps, OnDeleting est appelée pour tous ces éléments avant d'effectuer les suppressions.

     `IsDeleting` a la valeur True.

2.  La méthode <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> est appelée quand l'élément a été supprimé. Il reste dans le tas CLR pour qu'une opération d'annulation puisse être effectuée si nécessaire, mais il n'est plus lié aux autres éléments et est supprimé de `store.ElementDirectory`. Pour les relations, les rôles font toujours référencent les anciens acteurs de rôle.`IsDeleted` a la valeur true.

3.  Les méthode OnDeleting et OnDeleted sont appelées quand l'utilisateur appelle l'opération Annuler après avoir créé un élément et quand une suppression précédente est répétée dans Rétablir. Utilisez `this.Store.InUndoRedoOrRollback` pour éviter de mettre à jour les éléments du magasin dans ces cas-là. Pour plus d’informations, consultez [Comment : utiliser les Transactions pour mettre à jour le modèle](../modeling/how-to-use-transactions-to-update-the-model.md).

 Par exemple, le code suivant supprime un album quand son dernier morceau enfant est supprimé :

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

 Il est souvent plus utile de déclencher à partir de la suppression de la relation que de l'élément de rôle, car cela fonctionne à la fois quand l'élément est supprimé et quand la relation proprement dite est supprimée. Toutefois, pour une relation de référence, vous souhaiterez peut-être propager la suppression quand un élément associé est supprimé, mais pas quand la relation proprement dite est supprimée. Cet exemple supprime un album quand son dernier artiste collaborateur est supprimé, mais ne répond pas si les relations sont supprimées :

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

 Quand vous exécutez <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> sur un élément, OnDeleting et OnDeleted sont appelées. Ces méthodes sont toujours exécutées inline - autrement dit, juste avant et après la suppression réelle. Si votre code supprime plusieurs éléments, OnDeleting et OnDeleted sont appelées en alternance sur tous ces éléments les uns après les autres.

##  <a name="rules"></a> Événements et règles de suppression
 En guise d'alternative aux gestionnaires OnDelete, vous pouvez définir des règles de suppression des événements de suppression.

1.  **Suppression de** et **supprimer** règles sont déclenchées uniquement dans une transaction et non dans une annulation ou de rétablissement. Vous pouvez les configurer pour être mises en file d'attente pour s'exécuter à la fin de la transaction dans laquelle la suppression est effectuée. Les règles Deleting sont toujours exécutées avant toute règle Deleted qui se trouve dans la file d'attente.

     Utilisez des règles pour propager les modifications qui affectent uniquement des éléments du magasin, y compris des relations, des éléments de diagramme et leurs propriétés. En général, une règle Deleting sert à propager la suppression et une règle Delete sert à créer des relations et des éléments de remplacement.

     Pour plus d’informations, consultez [propager les modifications dans le modèle de règles](../modeling/rules-propagate-changes-within-the-model.md).

2.  **Supprimé** événement de magasin est appelé à la fin d’une transaction et est appelée après une annulation ou de rétablissement. Il peut donc servir à propager des suppressions à des objets en dehors du magasin, tels que des fichiers, des entrées de base de données ou d'autres objets dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

     Pour plus d’informations, consultez [gestionnaires propager les modifications en dehors le modèle d’événement](../modeling/event-handlers-propagate-changes-outside-the-model.md).

    > [!WARNING]
    >  Quand un élément a été supprimé, vous pouvez accéder à ses valeurs de propriété de domaine, mais vous ne pouvez pas naviguer parmi les liens de relations. Toutefois, si vous avez défini un événement deleted sur une relation, vous pouvez aussi accéder aux deux éléments qui étaient ses acteurs de rôle. Ainsi, si vous voulez répondre à la suppression d'un élément de modèle mais que vous souhaitez accéder un élément auquel il était lié, définissez un événement delete sur la relation plutôt que sur la classe de domaine de l'élément de modèle.

### <a name="example-deletion-rules"></a>Exemple de règles de suppression

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

### <a name="example-deleted-event"></a>Exemple d'événement Deleted

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

##  <a name="unmerge"></a> Annuler la fusion
 L’opération qui attache un élément enfant à son parent est appelée *fusion*. Elle a lieu quand un nouvel élément ou groupe d'éléments est créé à partir de la boîte à outils, déplacé à partir d'une autre partie du modèle ou copié à partir du Presse-papiers. En plus de créer une relation d'incorporation entre le parent et son nouvel enfant, l'opération de fusion peut aussi configurer des relations supplémentaires, créer des éléments auxiliaires et définir des valeurs de propriétés dans les éléments. L'opération de fusion est encapsulée dans une directive EMD (Element Merge Directive).

 Une directive EMD encapsule aussi le complémentaires *unmerge* ou `MergeDisconnect` opération. Si vous avez un cluster d'éléments qui a été construit à l'aide d'une fusion, nous vous recommandons d'utiliser l'opération unmerge associée pour supprimer un élément de ce cluster si vous souhaitez conserver les éléments restants dans un état cohérent. L'opération unmerge applique en général les techniques décrites dans les sections précédentes.

 Pour plus d’informations, consultez [personnalisation de la création d’élément et le déplacement des](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Voir aussi

- [Personnalisation du comportement de la copie](../modeling/customizing-copy-behavior.md)
- [Personnalisation de la création et du mouvement des éléments](../modeling/customizing-element-creation-and-movement.md)
- [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)