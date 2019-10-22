---
title: 'Comment : utiliser des transactions pour mettre à jour le modèle'
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a08ea67477f42008c35b6f141351beaeee03d27b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661137"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Comment : utiliser des transactions pour mettre à jour le modèle
Les transactions permettent de s’assurer que les modifications apportées au magasin sont traitées comme un groupe. Les modifications regroupées peuvent être validées ou restaurées en tant qu’unité unique.

 Chaque fois que le code de votre programme modifie, ajoute ou supprime un élément du magasin dans le kit de développement logiciel de visualisation et de modélisation Visual Studio, il doit le faire à l’intérieur d’une transaction. Il doit y avoir une instance active de <xref:Microsoft.VisualStudio.Modeling.Transaction> associée au magasin lorsque la modification se produit. Cela s’applique à tous les éléments de modèle, relations, formes, diagrammes et leurs propriétés.

 Le mécanisme de transaction vous aide à éviter les États incohérents. Si une erreur se produit pendant une transaction, toutes les modifications sont annulées. Si l’utilisateur exécute une commande Undo, chaque transaction récente est traitée comme une seule étape. L’utilisateur ne peut pas annuler des parties d’une modification récente, sauf si vous les placez explicitement dans des transactions distinctes.

## <a name="opening-a-transaction"></a>Ouverture d’une transaction
 La méthode la plus pratique pour gérer une transaction consiste à utiliser une instruction `using` placée dans une instruction `try...catch` :

```csharp
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Si une exception qui empêche le `Commit()` final se produit pendant les modifications, le magasin sera rétabli à son état précédent. Cela vous permet de vous assurer que les erreurs ne laissent pas le modèle dans un état incohérent.

 Vous pouvez effectuer un nombre quelconque de modifications dans une transaction. Vous pouvez ouvrir de nouvelles transactions dans une transaction active. Les transactions imbriquées doivent être validées ou restaurées avant la fin de la transaction conteneur. Pour plus d’informations, consultez l’exemple de la propriété <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A>.

 Pour rendre vos modifications permanentes, vous devez `Commit` la transaction avant qu’elle ne soit supprimée. Si une exception qui n’est pas interceptée à l’intérieur de la transaction se produit, le magasin est rétabli à son état avant les modifications.

## <a name="rolling-back-a-transaction"></a>Restauration d'une transaction
 Pour vous assurer que le magasin reste dans ou qu’il revient à son état avant la transaction, vous pouvez utiliser l’une de ces tactiques :

1. Lève une exception qui n’est pas interceptée à l’intérieur de la portée de la transaction.

2. Restaurez explicitement la transaction :

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>Les transactions n’affectent pas les objets non stockés
 Les transactions gouvernent uniquement l’état du magasin. Ils ne peuvent pas annuler les modifications partielles apportées aux éléments externes, tels que les fichiers, les bases de données ou les objets que vous avez déclarés avec des types ordinaires en dehors de la définition DSL.

 Si une exception peut entraîner une telle modification incohérente avec le magasin, vous devez gérer cette possibilité dans le gestionnaire d’exceptions. Une façon de s’assurer que les ressources externes restent synchronisées avec les objets Store consiste à coupler chaque objet externe à un élément stocké en utilisant des gestionnaires d’événements. Pour plus d’informations, consultez les [gestionnaires d’événements propagent les modifications en dehors du modèle](../modeling/event-handlers-propagate-changes-outside-the-model.md).

## <a name="rules-fire-at-the-end-of-a-transaction"></a>Les règles se déclenchent à la fin d’une transaction
 À la fin d’une transaction, avant que la transaction ne soit supprimée, les règles attachées aux éléments du magasin sont déclenchées. Chaque règle est une méthode appliquée à un élément de modèle qui a changé. Par exemple, il existe des règles de « correction » qui mettent à jour l’état d’une forme lorsque son élément de modèle a changé, et qui créent une forme lorsqu’un élément de modèle est créé. Il n’existe aucun ordre d’activation spécifié. Une modification effectuée par une règle peut déclencher une autre règle.

 Vous pouvez définir vos propres règles. Pour plus d’informations sur les règles, consultez [réponse aux modifications et propagation](../modeling/responding-to-and-propagating-changes.md).

 Les règles ne sont pas activées après une commande d’annulation, de rétablissement ou de restauration.

## <a name="transaction-context"></a>Contexte de transaction
 Chaque transaction contient un dictionnaire dans lequel vous pouvez stocker toutes les informations que vous souhaitez :

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 Cela est particulièrement utile pour transférer des informations entre des règles.

## <a name="transaction-state"></a>État de la transaction
 Dans certains cas, vous devez éviter de propager une modification si la modification est due à l’inactivité ou à la réopération d’une transaction. Cela peut se produire, par exemple, si vous écrivez un gestionnaire de valeurs de propriété qui peut mettre à jour une autre valeur dans le magasin. Étant donné que l’opération d’annulation réinitialise toutes les valeurs du magasin à leurs États précédents, il n’est pas nécessaire de calculer les valeurs mises à jour. Utilisez ce code :

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 Les règles peuvent se déclencher lors du chargement initial du magasin à partir d’un fichier. Pour éviter de répondre à ces changements, utilisez :

```csharp
if (!this.Store.InSerializationTransaction) {...}
```