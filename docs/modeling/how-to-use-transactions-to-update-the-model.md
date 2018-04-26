---
title: 'Comment : utiliser des transactions pour mettre à jour le modèle'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 590c355d391516def8f65579e5346281e335eea8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Comment : utiliser des transactions pour mettre à jour le modèle
Les transactions vous assurer que les modifications qui ont été apportées dans le magasin sont traitées en tant que groupe. Les modifications qui sont regroupées peuvent être validées ou restaurées en tant qu’unité unique.

 Chaque fois que votre code de programme modifie, ajoute ou supprime un élément dans le magasin [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK, il doit le faire à l’intérieur d’une transaction. Il doit y avoir une instance active de <xref:Microsoft.VisualStudio.Modeling.Transaction> associé au magasin lorsque la modification se produit. Cela s’applique à tous les éléments de modèle, des relations, des formes, des diagrammes et leurs propriétés.

 Le mécanisme de transaction permet d’éviter des états instables. Si une erreur se produit lors d’une transaction, toutes les modifications sont annulées. Si l’utilisateur exécute une commande d’annulation, chaque transaction récente est traitée comme une seule étape. L’utilisateur ne peut pas annuler les parties d’une modification récente, sauf si vous les placez dans des transactions distinctes.

## <a name="opening-a-transaction"></a>Ouverture d’une transaction
 La méthode la plus commode de gérer une transaction est un `using` instruction entre dans un `try...catch` instruction :

```
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

 Si une exception qui empêche le dernier `Commit()` se produit pendant les modifications, le magasin sera réinitialisé à son état précédent. Cela vous permet de vous assurer que les erreurs ne laissent pas le modèle dans un état incohérent.

 Vous pouvez effectuer n’importe quel nombre de modifications à l’intérieur d’une transaction. Vous pouvez ouvrir les nouvelles transactions à l’intérieur d’une transaction active. Les transactions imbriquées doivent valider ou annuler avant la fin de la transaction qui le contient. Pour plus d’informations, consultez l’exemple de la <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> propriété.

 Pour conserver vos modifications, vous devez `Commit` la transaction avant sa suppression. Si une exception se produit qui n’est pas interceptée à l’intérieur de la transaction, le magasin réinitialisera à son état avant les modifications.

## <a name="rolling-back-a-transaction"></a>Restauration d'une transaction
 Pour vous assurer que le magasin conserve ou retrouve son état avant la transaction, vous pouvez utiliser une de ces tactiques :

1.  Déclencher une exception qui n’est pas interceptée dans la portée de la transaction.

2.  Restaurer explicitement la transaction :

    ```
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>Les transactions n’affectent pas les objets de magasin Non
 Transactions régissent uniquement l’état de la banque. Ils ne peuvent pas annuler les modifications partielles ont été apportées à des éléments externes tels que des fichiers, des bases de données ou des objets que vous avez déclarés avec des types ordinaires en dehors de la définition DSL.

 Si une exception peut ne pas une telle modification incompatible avec le magasin, vous devez répondre à cette éventualité dans le Gestionnaire d’exceptions. Une pour vous assurer que les ressources externes restent synchronisés avec les objets de magasin consiste à associer chaque objet externe à un élément dans le magasin à l’aide de gestionnaires d’événements. Pour plus d’informations, consultez [gestionnaires propager les modifications en dehors du modèle d’événement](../modeling/event-handlers-propagate-changes-outside-the-model.md).

## <a name="rules-fire-at-the-end-of-a-transaction"></a>Feu de règles à la fin d’une Transaction
 À la fin d’une transaction, avant la suppression de la transaction, les règles associées à des éléments dans le magasin sont déclenchés. Chaque règle est une méthode qui est appliquée à un élément de modèle qui a changé. Par exemple, il existe des règles « corriger » pour mettre à jour l’état d’une forme lorsque son élément de modèle a été modifiée, et qui créent une forme lors de la création d’un élément de modèle. Il n’existe aucun ordre d’activation spécifié. Une modification apportée par une règle peut se déclencher une autre règle.

 Vous pouvez définir vos propres règles. Pour plus d’informations sur les règles, consultez [réponse aux et propager les modifications](../modeling/responding-to-and-propagating-changes.md).

 Les règles ne sont pas activent après une opération d’annulation, une restauration par progression ou une commande de restauration.

## <a name="transaction-context"></a>Contexte de transaction
 Chaque transaction a un dictionnaire dans lequel vous pouvez stocker les informations souhaitées :

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 Cela est particulièrement utile pour transférer des informations entre les règles.

## <a name="transaction-state"></a>État de la transaction
 Dans certains cas, de que vous devez éviter propager une modification si la modification est dû à une annulation ou le rétablissement d’une transaction. Cela peut se produire, par exemple, si vous écrivez un gestionnaire de valeur de propriété qui peut mettre à jour une autre valeur dans le magasin. Étant donné que l’opération d’annulation réinitialise toutes les valeurs dans le magasin à leur état, il n’est pas nécessaire calculer les valeurs mises à jour. Utilisez ce code :

```
if (!this.Store.InUndoRedoOrRollback) {...}
```

 Règles peuvent se déclencher lorsque le magasin est initialement chargé à partir d’un fichier. Pour éviter de répondre à ces modifications, utilisez :

```
if (!this.Store.InSerializationTransaction) {...}

```