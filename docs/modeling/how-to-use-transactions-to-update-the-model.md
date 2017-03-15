---
title: "Comment&#160;: utiliser des transactions pour mettre &#224; jour le mod&#232;le | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 7
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 7
---
# Comment&#160;: utiliser des transactions pour mettre &#224; jour le mod&#232;le
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les transactions de garantir que les modifications apportées au magasin sont traitées en tant que groupe.  Change qui sont regroupés peut être validé ou annulé en procédant comme une seule unité.  
  
 Chaque fois que votre code de programme modifie, ajoute, ou supprime un élément dans le magasin dans la visualisation de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et Kit de développement logiciel de modélisation, il doit le faire dans une transaction.  Il doit exister une instance active d' <xref:Microsoft.VisualStudio.Modeling.Transaction> associée à le magasin lorsque la modification se produit.  Cela s'applique à tous les éléments de modèle, des relations, à formes, à diagrammes, et à leurs propriétés.  
  
 Les outils de mécanisme de transaction vous évitez les rapports cohérents.  Si une erreur se produit pendant une transaction, toutes les modifications sont annulées.  Si l'utilisateur exécute une commande annuler, chaque transaction récente est traitée comme pas \- à \- pas.  L'utilisateur ne peut pas annuler les parties d'une modification récente, à moins que vous les avez mis explicitement dans des transactions distinctes.  
  
## ouvrir une transaction  
 La méthode la plus pratique de gérer une transaction consiste à utiliser une instruction d' `using` comprise dans une instruction d' `try...catch` :  
  
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
  
 Si une exception qui empêché `Commit()`final se produit lors de la modification, le magasin sera réinitialisée à son état précédent.  Cela vous permet de garantir que les erreurs laisser le modèle dans un état incohérent.  
  
 Vous pouvez apporter plusieurs modifications dans une transaction.  Vous pouvez ouvrir de nouveaux transactions dans une transaction active.  Les transactions imbriquées doivent valider ou annuler avant que la transaction conteneur se termine.  Pour plus d'informations, consultez l'exemple de la propriété d' <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> .  
  
 Pour que votre constante de modifications, vous devez `Commit` la transaction avant qu'elle soit supprimée.  Si une exception n'est pas interceptée dans la transaction, le magasin sera réinitialisée à son état avant que les modifications.  
  
## Restauration d'une transaction  
 Pour garantir que le magasin reste dans ou revient à son état avant la transaction, vous pouvez utiliser l'un ou l'autre de cette tactique :  
  
1.  Déclenchez une exception qui n'est pas interceptée dans la portée de la transaction.  
  
2.  Restaurer explicitement arrière la transaction :  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## Les transactions n'affectent pas les objets de la Non\-Banque  
 Les transactions régissent uniquement l'état de le magasin.  Ils ne peuvent pas annuler les modifications partielles apportées aux éléments externes tels que les fichiers, les bases de données, ou objets que vous avez déclarés avec les types ordinaires à l'extérieur de la définition de langage spécifique à un domaine.  
  
 Si une exception peut permettre à une modification non cohérente avec le magasin, vous devez traiter cette possibilité dans le gestionnaire d'exceptions.  Une façon de s'assurer que les ressources externes restent synchronisées avec les objets de magasin est d'associer chaque objet externe à un élément dans le magasin en utilisant des gestionnaires d'événements.  Pour plus d'informations, consultez [Propagation de modifications en dehors du modèle par des gestionnaires d'événements](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
## Les règles se déclenchent à la fin d'une transaction  
 À la fin d'une transaction, avant que la transaction soit supprimée, les règles jointes aux éléments dans le magasin sont déclenchés.  chaque règle est une méthode qui est appliquée à un élément de modèle qui a changé.  Par exemple, il y a « résolvent » des règles qui mettent à jour l'état d'une forme lorsque son élément de modèle a changé, et qui créent une forme lorsqu'un élément de modèle est créé.  Il n'y avait pas de commande de mise à déclencher spécifiée.  Une modification apportée par une règle peut déclencher une autre règle.  
  
 vous pouvez définir vos propres règles.  Pour plus d'informations sur les règles, consultez [Propagation et réponse aux modifications en attente](../modeling/responding-to-and-propagating-changes.md).  
  
 Les règles ne les déclenchent pas après une annulation, de rétablissement, ou une commande de restauration.  
  
## Contexte transaction  
 Chaque transaction a un dictionnaire dans lequel vous pouvez stocker toutes les informations que vous voulez :  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 Cela est particulièrement utile pour transférer des informations entre les règles.  
  
## État de la transaction  
 Dans certains cas vous devez éviter de propager une modification si la modification a été provoquée en annulant ou en refaisant une transaction.  Cela peut se produire, par exemple, si vous écrivez un gestionnaire de valeur de propriété qui peut mettre à jour une autre valeur dans le magasin.  Étant donné que l'opération d'annulation réinitialise toutes les valeurs dans le magasin à leurs états antérieurs, il n'est pas nécessaire de calculer des valeurs mises à jour.  utilisez ce code :  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 Les règles peuvent se déclencher lorsque le magasin initialement sont chargées à partir d'un fichier.  Pour éviter de répondre à ces modifications, utilisez :  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```