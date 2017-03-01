---
title: "Gestionnaires d’événements propagent les modifications en dehors du modèle | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
ms.assetid: 0ac8d1e4-239f-4370-ba1d-3769bb38b8a5
caps.latest.revision: 18
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: af5fbd8973082e92f9609e335314a30eb22595fa
ms.lasthandoff: 02/22/2017

---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Propagation de modifications en dehors du modèle par des gestionnaires d'événements
Dans Visualization and Modeling SDK, vous pouvez définir des gestionnaires d’événements de magasin pour propager les modifications apportées aux ressources en dehors du magasin, telles que les variables non magasin, des fichiers modèles dans d’autres magasins, ou d’autres [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensions. Gestionnaires d’événements de magasin sont exécutées après la fin de la transaction dans laquelle l’événement déclencheur s’est produite. Ils sont également exécutées dans une opération d’annulation ou de rétablissement. Par conséquent, contrairement aux règles de magasin, événements de la banque sont particulièrement utiles pour la mise à jour des valeurs qui sont en dehors du magasin. Contrairement aux événements .NET, magasin de gestionnaires d’événements sont inscrits pour écouter une classe : vous n’avez pas à inscrire un gestionnaire différent pour chaque instance. Pour plus d’informations sur le choix entre plusieurs méthodes de gestion des modifications, consultez [réponse aux et propager les modifications](../modeling/responding-to-and-propagating-changes.md).  
  
 La surface du graphique et autres contrôles d’interface utilisateur sont des exemples de ressources externes qui peuvent être gérés par les événements de magasin.  
  
### <a name="to-define-a-store-event"></a>Pour définir un événement de magasin  
  
1.  Choisissez le type d’événement que vous souhaitez surveiller. Pour obtenir une liste complète, consultez les propriétés du <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>.</xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory> Chaque propriété correspond à un type d’événement. Les plus fréquemment utilisés sont des types des événements :  
  
    -   `ElementAdded`– déclenché lorsqu’un élément de modèle, lien de relation, une forme ou connecteur est créé.  
  
    -   ElementPropertyChanged – déclenché lorsque la valeur d’un `Normal` propriété de domaine est modifiée. L’événement est déclenché uniquement si les valeurs nouvelles et anciennes ne sont pas égales. L’événement ne peut pas être appliqué aux propriétés de stockage calculées et personnalisées.  
  
         Il ne peut pas être appliqué aux propriétés du rôle qui correspondent à des liens de relation. Au lieu de cela, utilisez `ElementAdded` pour analyser la relation de domaine.  
  
    -   `ElementDeleted`– déclenché après un élément de modèle, forme, relation ou le lien a été supprimé. Vous pouvez accéder à la valeur de l’élément, mais il n’aura pas de relations à d’autres éléments.  
  
2.  Ajoutez une définition de classe partielle pour *Votre_solution_dsl***DocData** dans un fichier de code séparé dans le **DslPackage** projet.  
  
3.  Écrivez le code de l’événement comme une méthode, comme dans l’exemple suivant. Il peut être `static`, sauf si vous souhaitez accéder à `DocData`.  
  
4.  Substituer `OnDocumentLoaded()` pour inscrire le gestionnaire. Si vous avez plusieurs gestionnaires, vous pouvez les enregistrer toutes dans le même emplacement.  
  
 L’emplacement du code d’enregistrement n’est pas critique. `DocView.LoadView()`est un autre emplacement.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.MusicLib  
{  
  partial class MusicLibDocData  
  {  
    // Register store events here or in DocView.LoadView().  
    protected override void OnDocumentLoaded()  
    {  
      base.OnDocumentLoaded(); // Don’t forget this.  
  
      #region Store event handler registration.       
      Store store = this.Store;  
      EventManagerDirectory emd = store.EventManagerDirectory;  
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory  
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));  
      emd.ElementAdded.Add(linkInfo,   
          new EventHandler<ElementAddedEventArgs>(AddLink));  
      emd.ElementDeleted.Add(linkInfo,   
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));  
  
      #endregion Store event handlers.  
    }  
  
    private void AddLink(object sender, ElementAddedEventArgs e)  
    {  
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;  
      if (link != null)   
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);  
    }  
    private void RemoveLink(object sender, ElementDeletedEventArgs e)  
    {  
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;  
      if (link != null)   
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);  
    }  
  }  
  
}  
  
```  
  
## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>L’utilisation d’événements pour effectuer des ajustements irréalisable dans le magasin  
 Événements de la banque ne sont pas normalement utilisés pour propager des modifications à l’intérieur de la banque, parce que le Gestionnaire d’événements s’exécute après que la transaction est validée. Au lieu de cela, vous utiliseriez une règle du magasin. Pour plus d’informations, consultez [propager les modifications dans le modèle de règles](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Toutefois, vous pouvez utiliser un gestionnaire d’événements pour effectuer des mises à jour supplémentaires au magasin, si vous souhaitez que l’utilisateur soit en mesure d’annuler les mises à jour supplémentaires séparément à partir de l’événement d’origine. Par exemple, supposons que les caractères minuscules sont la convention habituelle pour les titres d’album. Vous pouvez écrire un gestionnaire d’événements de magasin qui corrige le titre en minuscules après que l’utilisateur a tapé en majuscules. Mais l’utilisateur peut utiliser la commande Annuler pour annuler la correction, la restauration des caractères majuscules. Une annulation deuxième supprimerait la modification de l’utilisateur.  
  
 En revanche, si vous avez écrit une règle de magasin pour faire la même chose, modification de l’utilisateur et la correction serait dans la même transaction, afin que l’utilisateur n’a pas pu annuler l’ajustement sans perdre la modification d’origine.  
  
```  
  
partial class MusicLibDocView  
{  
    // Register store events here or in DocData.OnDocumentLoaded().  
    protected override void LoadView()  
    {  
      /* Register store event handler for Album Title property. */  
      // Get reflection data for property:  
      DomainPropertyInfo propertyInfo =   
        this.DocData.Store.DomainDataDirectory  
        .FindDomainProperty(Album.TitleDomainPropertyId);  
      // Add to property handler list:  
      this.DocData.Store.EventManagerDirectory  
        .ElementPropertyChanged.Add(propertyInfo,  
        new EventHandler<ElementPropertyChangedEventArgs>  
             (AlbumTitleAdjuster));  
  
      /*  
      // Alternatively, you can set one handler for   
      // all properties of a class.  
      // Your handler has to determine which property changed.  
      DomainClassInfo classInfo = this.Store.DomainDataDirectory  
           .FindDomainClass(typeof(Album));  
      this.Store.EventManagerDirectory  
          .ElementPropertyChanged.Add(classInfo,  
        new EventHandler<ElementPropertyChangedEventArgs>  
             (AlbumTitleAdjuster));  
       */  
      return base.LoadView();  
    }  
  
// Undoable adjustment after a property is changed.   
// Method can be static since no local access.  
private static void AlbumTitleAdjuster(object sender,  
         ElementPropertyChangedEventArgs e)  
{  
  Album album = e.ModelElement as Album;  
  Store store = album.Store;  
  
  // We mustn't update the store in an Undo:  
  if (store.InUndoRedoOrRollback   
      || store.InSerializationTransaction)  
      return;  
  
  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)  
  {  
    string newValue = (string)e.NewValue;  
    string lowerCase = newValue.ToLowerInvariant();  
    if (!newValue.Equals(lowerCase))  
    {  
      using (Transaction t = store.TransactionManager  
            .BeginTransaction("adjust album title"))  
      {  
        album.Title = lowerCase;  
        t.Commit();  
      } // Beware! This could trigger the event again.  
    }  
  }  
  // else other properties of this class.  
}  
  
```  
  
 Si vous écrivez un événement qui met à jour le magasin :  
  
-   Utilisez `store.InUndoRedoOrRollback` afin d’éviter d’apporter des modifications aux éléments de modèle d’annulation. Le Gestionnaire de transactions configurera tout dans le magasin à son état d’origine.  
  
-   Utilisez `store.InSerializationTransaction` afin d’éviter d’apporter des modifications pendant que le modèle est chargé à partir du fichier.  
  
-   Vos modifications provoquent davantage d’événements à déclencher. Veillez à éviter une boucle infinie.  
  
## <a name="store-event-types"></a>Stocker les types d’événements  
 Chaque type d’événement correspond à un regroupement dans Store.EventManagerDirectory. Vous pouvez ajouter ou supprimer des gestionnaires d’événements à tout moment, mais il est courant pour les ajouter lorsque le document est chargé.  
  
|`EventManagerDirectory`Nom de propriété|Exécuté lorsque|  
|-------------------------------------------|-------------------|  
|ElementAdded|Une instance d’une classe de domaine, une relation de domaine, forme, connecteur ou diagramme est créée.|  
|ElementDeleted|Un élément de modèle a été supprimé du répertoire des éléments du magasin et n’est plus la source ou la cible d’une relation. L’élément n’est pas réellement supprimé de la mémoire, mais est conservée dans le cas d’une annulation ultérieure.|  
|ElementEventsBegun|Appelé à la fin d’une transaction externe.|  
|ElementEventsEnded|Appelé lorsque tous les autres événements ont été traitées.|  
|ElementMoved|Un élément de modèle a été déplacé à partir de la partition d’un magasin à l’autre.<br /><br /> Cela n’est pas lié à l’emplacement d’une forme sur le diagramme.|  
|ElementPropertyChanged|La valeur d’une propriété de domaine a changé. Il est exécuté uniquement si les valeurs anciennes et nouvelles sont inégales.|  
|RolePlayerChanged|L’un des deux rôles (fin) d’une relation fait référence à un nouvel élément.|  
|RolePlayerOrderChanged|Dans un rôle avec la multiplicité est supérieure à 1, la séquence de liens a changé.|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## <a name="see-also"></a>Voir aussi  
 [Répondre à et propagation des modifications](../modeling/responding-to-and-propagating-changes.md)   
 [Exemple de code : diagrammes de Circuit](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 

