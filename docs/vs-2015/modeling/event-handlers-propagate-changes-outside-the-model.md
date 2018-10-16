---
title: Gestionnaires d’événements propagent les modifications en dehors du modèle | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
ms.assetid: 0ac8d1e4-239f-4370-ba1d-3769bb38b8a5
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 38958aae1c2449145107faa7abe00a2d86baaa9a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303197"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Propagation de modifications en dehors du modèle par des gestionnaires d'événements
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visualization and Modeling SDK, vous pouvez définir des gestionnaires d’événements de magasin pour propager les modifications apportées aux ressources en dehors du magasin, telles que les variables non-store, des fichiers de modèles dans d’autres magasins, ou d’autres [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensions. Gestionnaires d’événements Store sont exécutés après la fin de la transaction dans laquelle l’événement de déclenchement s’est produite. Elles sont également exécutées en une opération d’annulation ou de rétablissement. Par conséquent, contrairement au magasin de règles, événements de stockage sont particulièrement utiles pour la mise à jour des valeurs qui sont en dehors du magasin. Contrairement aux événements de .NET, les gestionnaires d’événements de magasin sont inscrit pour écouter à une classe : vous n’avez pas à inscrire un gestionnaire distinct pour chaque instance. Pour plus d’informations sur comment choisir entre les différentes façons de gérer les modifications, consultez [réponse en cours à et propagation des modifications](../modeling/responding-to-and-propagating-changes.md).  
  
 La surface graphique et autres contrôles d’interface utilisateur sont des exemples de ressources externes qui peuvent être gérés par les événements de magasin.  
  
### <a name="to-define-a-store-event"></a>Pour définir un événement de magasin  
  
1.  Choisissez le type d’événement que vous souhaitez surveiller. Pour obtenir une liste complète, consultez les propriétés de <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Chaque propriété correspond à un type d’événement. Les plus fréquemment utilisés sont des types des événements :  
  
    -   `ElementAdded` – déclenché lorsqu’un élément de modèle, lien de relation, forme ou un connecteur est créé.  
  
    -   ElementPropertyChanged – déclenché lorsque la valeur d’un `Normal` de propriété de domaine est modifiée. L’événement est déclenché uniquement si les valeurs anciennes et nouvelles ne sont pas égales. L’événement ne peut pas être appliqué aux propriétés de stockage calculées et personnalisées.  
  
         Il ne peut pas être appliqué aux propriétés du rôle qui correspondent aux liens de relation. Au lieu de cela, utilisez `ElementAdded` pour surveiller la relation de domaine.  
  
    -   `ElementDeleted` – déclenché après un élément de modèle, relation, forme ou le lien a été supprimé. Vous pouvez toujours accéder les valeurs de propriété de l’élément, mais il n’aura pas de relations à d’autres éléments.  
  
2.  Ajoutez une définition de classe partielle pour _Votre_solution_dsl_**DocData** dans un fichier de code séparé dans le **DslPackage** projet.  
  
3.  Écrivez le code de l’événement comme une méthode, comme dans l’exemple suivant. Il peut être `static`, sauf si vous souhaitez accéder à `DocData`.  
  
4.  Substituer `OnDocumentLoaded()` pour inscrire le gestionnaire. Si vous avez plusieurs gestionnaires, vous pouvez les inscrire dans le même emplacement.  
  
 L’emplacement du code d’inscription n’est pas critique. `DocView.LoadView()` est un autre emplacement.  
  
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
  
## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>À l’aide d’événements pour effectuer des ajustements annulables dans le Store  
 Store événements ne sont pas normalement utilisés pour la propagation des modifications à l’intérieur du magasin, étant donné que le Gestionnaire d’événements s’exécute après que la transaction est validée. Au lieu de cela, vous utiliseriez une règle de magasin. Pour plus d’informations, consultez [propager les modifications dans le modèle de règles](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Toutefois, vous pouvez utiliser un gestionnaire d’événements pour effectuer des mises à jour supplémentaires dans le magasin, si vous souhaitez que l’utilisateur peut annuler les mises à jour supplémentaires séparément à partir de l’événement d’origine. Par exemple, supposons que les caractères minuscules sont la convention habituelle pour les titres d’album. Vous pouvez écrire un gestionnaire d’événements de magasin qui corrige le titre en minuscules, une fois que l’utilisateur a tapé en majuscules. Mais l’utilisateur peut utiliser la commande Annuler pour annuler votre correction, restauration les caractères majuscules. Une deuxième annulation supprimerait la modification de l’utilisateur.  
  
 En revanche, si vous avez écrit une règle de magasin pour faire la même chose, modification de l’utilisateur et votre correction serait dans la même transaction, afin que l’utilisateur n’a pas pu annuler l’ajustement sans perdre la modification d’origine.  
  
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
  
-   Utilisez `store.InUndoRedoOrRollback` pour éviter d’effectuer des modifications aux éléments de modèle d’annulation. Le Gestionnaire de transactions tous les éléments figurant dans le magasin à son état d’origine.  
  
-   Utilisez `store.InSerializationTransaction` afin d’éviter d’apporter des modifications pendant que le modèle est chargé à partir du fichier.  
  
-   Vos modifications entraîne davantage d’événements à déclencher. Veillez à éviter une boucle infinie.  
  
## <a name="store-event-types"></a>Types d’événements Store  
 Chaque type d’événement correspond à une collection dans Store.EventManagerDirectory. Vous pouvez ajouter ou supprimer des gestionnaires d’événements à tout moment, mais il est habituel pour les ajouter lorsque le document est chargé.  
  
|`EventManagerDirectory` Nom de propriété|Exécuté lorsque|  
|-------------------------------------------|-------------------|  
|ElementAdded|Une instance d’une classe de domaine, une relation de domaine, forme, connecteur ou diagramme est créée.|  
|ElementDeleted|Un élément de modèle a été supprimé du répertoire d’éléments du magasin et n’est plus la source ou la cible d’une relation. L’élément n’est pas réellement supprimé de la mémoire, mais est conservée dans le cas d’une opération d’annulation ultérieure.|  
|ElementEventsBegun|Appelé à la fin d’une transaction externe.|  
|Événement ElementEventsEnded|Appelé lorsque tous les autres événements ont été traitées.|  
|ElementMoved|Un élément de modèle a été déplacé à partir de la partition d’un magasin vers un autre.<br /><br /> Cela n’est pas lié à l’emplacement d’une forme sur le diagramme.|  
|ElementPropertyChanged|La valeur d’une propriété de domaine a changé. Cela est exécutée uniquement si les valeurs anciennes et nouvelles sont inégales.|  
|RolePlayerChanged|Un des deux rôles (fin) d’une relation de fait référence à un nouvel élément.|  
|RolePlayerOrderChanged|Dans un rôle avec la multiplicité est supérieure à 1, la séquence de liens a changé.|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## <a name="see-also"></a>Voir aussi  
 [Propagation des modifications et réponse aux](../modeling/responding-to-and-propagating-changes.md)   
 [Exemple de code : diagrammes de Circuit](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)



