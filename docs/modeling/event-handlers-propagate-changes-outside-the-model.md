---
title: Propagation de modifications en dehors du modèle par des gestionnaires d'événements
description: Découvrez que dans le kit de développement logiciel de visualisation et de modélisation, vous pouvez définir des gestionnaires d’événements Store pour propager les modifications vers les ressources en dehors du magasin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 115d26840f321792712392367794e443e41543a2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388943"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Propagation de modifications en dehors du modèle par des gestionnaires d'événements

Dans le kit de développement logiciel de visualisation et de modélisation, vous pouvez définir des gestionnaires d’événements de magasin pour propager les modifications vers les ressources en dehors du magasin, telles que les variables non stockées, les fichiers, les modèles dans d’autres magasins ou d’autres extensions Visual Studio. Les gestionnaires d’événements Store sont exécutés après la fin de la transaction dans laquelle l’événement de déclenchement s’est produit. Elles sont également exécutées lors d’une opération d’annulation ou de rétablissement. Par conséquent, contrairement aux règles de magasin, les événements de magasin sont particulièrement utiles pour mettre à jour des valeurs qui se trouvent en dehors du magasin. Contrairement aux événements .NET, les gestionnaires d’événements de magasin sont inscrits pour écouter une classe : vous n’avez pas besoin d’inscrire un gestionnaire distinct pour chaque instance. Pour plus d’informations sur le choix entre les différentes façons de gérer les modifications, consultez [réponse aux modifications et propagation](../modeling/responding-to-and-propagating-changes.md).

La surface graphique et les autres contrôles d’interface utilisateur sont des exemples de ressources externes qui peuvent être gérées par les événements de stockage.

### <a name="to-define-a-store-event"></a>Pour définir un événement de magasin

1. Choisissez le type d’événement que vous souhaitez analyser. Pour obtenir une liste complète, examinez les propriétés de <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory> . Chaque propriété correspond à un type d’événement. Les types d’événements les plus fréquemment utilisés sont les suivants :

    - `ElementAdded` -déclenché lors de la création d’un élément de modèle, d’un lien de relation, d’une forme ou d’un connecteur.

    - ElementPropertyChanged-déclenché lorsque la valeur d’une `Normal` propriété de domaine est modifiée. L’événement est déclenché uniquement si les valeurs nouvelles et anciennes ne sont pas égales. L’événement ne peut pas être appliqué aux propriétés de stockage calculées et personnalisées.

         Il ne peut pas être appliqué aux propriétés de rôle qui correspondent à des liens de relation. À la place, utilisez `ElementAdded` pour surveiller la relation de domaine.

    - `ElementDeleted` -déclenché après la suppression d’un élément de modèle, d’une relation, d’une forme ou d’un connecteur. Vous pouvez toujours accéder aux valeurs de propriété de l’élément, mais il n’aura aucune relation avec d’autres éléments.

2. Ajoutez une définition de classe partielle pour _YourDsl_**DocData** dans un fichier de code séparé dans le projet **DslPackage** .

3. Écrivez le code de l’événement sous la forme d’une méthode, comme dans l’exemple suivant. Il peut s’agir de `static` , sauf si vous souhaitez accéder à `DocData` .

4. Substituez `OnDocumentLoaded()` pour inscrire le gestionnaire. Si vous avez plus d’un gestionnaire, vous pouvez les inscrire dans le même emplacement.

L’emplacement du code d’inscription n’est pas critique. `DocView.LoadView()` est un autre emplacement.

```csharp
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
      base.OnDocumentLoaded(); // Don't forget this.

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

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Utiliser des événements pour effectuer des ajustements annulables dans le magasin

Les événements de magasin ne sont normalement pas utilisés pour propager les modifications dans le magasin, car le gestionnaire d’événements s’exécute une fois la transaction validée. Au lieu de cela, vous devez utiliser une règle de magasin. Pour plus d’informations, consultez [règles de propagation des modifications dans le modèle](../modeling/rules-propagate-changes-within-the-model.md).

Toutefois, vous pouvez utiliser un gestionnaire d’événements pour effectuer des mises à jour supplémentaires du magasin, si vous souhaitez que l’utilisateur soit en mesure d’annuler les mises à jour supplémentaires séparément de l’événement d’origine. Supposons, par exemple, que les caractères minuscules constituent la Convention habituelle pour les titres d’albums. Vous pouvez écrire un gestionnaire d’événements Store qui corrige le titre en minuscules après que l’utilisateur l’a tapé en majuscules. Toutefois, l’utilisateur peut utiliser la commande Annuler pour annuler votre correction, en restaurant les caractères majuscules. Une deuxième opération d’annulation supprimerait la modification de l’utilisateur.

En revanche, si vous avez écrit une règle de magasin pour faire la même chose, la modification de l’utilisateur et votre correction se trouvent dans la même transaction, de sorte que l’utilisateur n’a pas pu annuler l’ajustement sans perdre la modification d’origine.

```csharp
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

- Utilisez `store.InUndoRedoOrRollback` pour éviter d’apporter des modifications aux éléments de modèle dans Undo. Le gestionnaire de transactions va rétablir l’état d’origine de tous les éléments du magasin.

- Utilisez `store.InSerializationTransaction` pour éviter d’apporter des modifications pendant le chargement du modèle à partir d’un fichier.

- Vos modifications entraînent le déclenchement d’événements supplémentaires. Veillez à éviter une boucle infinie.

## <a name="store-event-types"></a>Types d’événements Store

Chaque type d’événement correspond à une collection dans Store. EventManagerDirectory. Vous pouvez ajouter ou supprimer des gestionnaires d’événements à tout moment, mais il est habituel de les ajouter lorsque le document est chargé.

|`EventManagerDirectory` Nom de la propriété|Exécuté lorsque|
|-|-|
|ElementAdded|Une instance d’une classe de domaine, relation de domaine, forme, connecteur ou diagramme est créée.|
|ElementDeleted|Un élément de modèle a été supprimé du répertoire de l’élément du magasin et n’est plus la source ou la cible d’une relation. L’élément n’est pas réellement supprimé de la mémoire, mais il est conservé en cas d’annulation ultérieure.|
|ElementEventsBegun|Appelée à la fin d’une transaction externe.|
|Un événement elementeventsended|Appelé lorsque tous les autres événements ont été traités.|
|ElementMoved|Un élément de modèle a été déplacé d’une partition de magasin à une autre.<br /><br /> Cela n’est pas lié à l’emplacement d’une forme sur le diagramme.|
|ElementPropertyChanged|La valeur d’une propriété de domaine a changé. Cette valeur est exécutée uniquement si les valeurs anciennes et nouvelles ne sont pas égales.|
|RolePlayerChanged|L’un des deux rôles (se termine) d’une relation fait référence à un nouvel élément.|
|RolePlayerOrderChanged|Dans un rôle dont la multiplicité est supérieure à 1, la séquence de liens a changé.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Voir aussi

- [Propagation et réponse aux modifications en attente](../modeling/responding-to-and-propagating-changes.md)
- [Exemple de code : diagrammes de circuit](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
