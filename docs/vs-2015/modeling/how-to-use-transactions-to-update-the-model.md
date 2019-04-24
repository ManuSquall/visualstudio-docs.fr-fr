---
title: 'Procédure : Utiliser des Transactions pour mettre à jour le modèle | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bbc09543d0ee0297678d3f205becc55a6b6d7714
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60085922"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Procédure : Utiliser des transactions pour mettre à jour le modèle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Transactions Assurez-vous que les modifications qui ont été apportées dans le magasin sont traitées en tant que groupe. Les modifications qui sont regroupées peuvent être validées ou restaurées en tant qu’unité unique.  
  
 Chaque fois que votre code de programme modifie, ajoute ou supprime un élément dans le Store dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK, elle doit le faire à l’intérieur d’une transaction. Il doit y avoir une instance active de <xref:Microsoft.VisualStudio.Modeling.Transaction> associé le Store lorsque la modification se produit. Cela s’applique à tous les éléments de modèle, relations, formes, diagrammes et leurs propriétés.  
  
 Le mécanisme de transaction vous permet d’éviter des états incohérents. Si une erreur se produit lors d’une transaction, toutes les modifications sont annulées. Si l’utilisateur exécute une commande d’annulation, chaque transaction récente est traitée comme une seule étape. L’utilisateur ne peut pas annuler les parties d’une modification récente, sauf si vous les placez dans des transactions distinctes.  
  
## <a name="opening-a-transaction"></a>Ouverture d’une transaction  
 La méthode la plus pratique de la gestion d’une transaction est avec un `using` instruction entre dans un `try...catch` instruction :  
  
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
  
 Si une exception qui empêche la dernière `Commit()` se produit pendant les modifications, le Store sera réinitialisée à son état précédent. Cela permet de s’assurer que les erreurs ne laissent pas le modèle dans un état incohérent.  
  
 Vous pouvez apporter autant de modifications à l’intérieur d’une seule transaction. Vous pouvez ouvrir les nouvelles transactions à l’intérieur d’une transaction active. Les transactions imbriquées doivent valider ou restaurer avant la fin de transaction qui le contient. Pour plus d’informations, consultez l’exemple de la <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> propriété.  
  
 Pour conserver vos modifications, vous devez `Commit` la transaction avant sa suppression. Si une exception se produit qui n’est pas interceptée dans la transaction, le Store réinitialisera à son état avant les modifications.  
  
## <a name="rolling-back-a-transaction"></a>Restauration d'une transaction  
 Pour vous assurer que le Store conserve ou revient à son état avant la transaction, vous pouvez utiliser une de ces tactiques :  
  
1. Déclencher une exception qui n’est pas interceptée dans la portée de la transaction.  
  
2. Restaurer explicitement la transaction :  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## <a name="transactions-do-not-affect-non-store-objects"></a>Les transactions n’affectent pas les objets Non Store  
 Transactions déterminent uniquement l’état de la Store. Ils ne peuvent pas annuler les modifications partielles qui ont été apportées à des éléments externes tels que les fichiers, les bases de données ou les objets que vous avez déclarés avec des types ordinaires en dehors de la définition DSL.  
  
 Si une exception peut ne pas une telle modification incohérent avec le Store, vous devez répondre à cette éventualité dans le Gestionnaire d’exceptions. Un pour vous assurer que les ressources externes restent synchronisés avec les objets Store consiste à associer chaque objet externe à un élément dans le magasin à l’aide de gestionnaires d’événements. Pour plus d’informations, consultez [gestionnaires propager les modifications en dehors le modèle d’événement](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
## <a name="rules-fire-at-the-end-of-a-transaction"></a>Feu de règles à la fin d’une Transaction  
 À la fin d’une transaction, avant que la transaction est supprimée, les règles associées aux éléments dans le magasin sont déclenchés. Chaque règle est une méthode qui est appliquée à un élément de modèle qui a changé. Par exemple, il existe des règles de « correction » qui mettent à jour l’état d’une forme lorsque son élément de modèle a changé, et qui créent une forme lors de la création d’un élément de modèle. Il n’existe aucun ordre d’activation spécifié. Une modification apportée par une règle peut se déclencher une autre règle.  
  
 Vous pouvez définir vos propres règles. Pour plus d’informations sur les règles, consultez [réponse en cours à et propagation des modifications](../modeling/responding-to-and-propagating-changes.md).  
  
 Les règles ne sont pas activés après une opération d’annulation, une opération de rétablissement ou une commande de restauration.  
  
## <a name="transaction-context"></a>Contexte de transaction  
 Chaque transaction a un dictionnaire dans lequel vous pouvez stocker les informations souhaitées :  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 Cela est particulièrement utile pour transférer des informations entre les règles.  
  
## <a name="transaction-state"></a>État de la transaction  
 Dans certains cas, de que vous devez éviter propager une modification si la modification est dû à une annulation ou de rétablissement d’une transaction. Cela peut se produire, par exemple, si vous écrivez un gestionnaire de valeur de propriété qui peut mettre à jour une autre valeur dans le Store. Étant donné que l’opération d’annulation réinitialise toutes les valeurs dans le Store à leur état précédent, il n’est pas nécessaire calculer les valeurs mises à jour. Utilisez ce code :  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 Règles peuvent être déclenché lorsque le magasin est initialement chargé à partir d’un fichier. Pour éviter de répondre à ces modifications, utilisez :  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```
