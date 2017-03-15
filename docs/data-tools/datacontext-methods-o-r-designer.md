---
title: "M&#233;thodes DataContext (Concepteur O/R) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 5
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# M&#233;thodes DataContext (Concepteur O/R)
Les méthodes <xref:System.Data.Linq.DataContext> \(dans le contexte du [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)\) sont des méthodes de la classe <xref:System.Data.Linq.DataContext> qui exécutent des procédures stockées et des fonctions dans une base de données.  
  
 La classe <xref:System.Data.Linq.DataContext> est une classe [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] qui agit comme un conduit entre une base de données SQL Server et les classes d'entité [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] mappées à cette base de données.La classe <xref:System.Data.Linq.DataContext> contient les informations de chaîne de connexion et les méthodes pour se connecter à une base de données et manipuler les données dans celle\-ci. Par défaut, la classe <xref:System.Data.Linq.DataContext> contient plusieurs méthodes que vous pouvez appeler, telles que la méthode <xref:System.Data.Linq.DataContext.SubmitChanges%2A> qui envoie des données mises à jour des classes [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] à la base de données.Vous pouvez également créer des méthodes <xref:System.Data.Linq.DataContext> supplémentaires pour mapper aux procédures stockées et aux fonctions.En d'autres termes, l'appel de ces méthodes personnalisées exécutera la procédure stockée ou la fonction dans la base de données à laquelle la méthode <xref:System.Data.Linq.DataContext> est mappée.Vous pouvez ajouter de nouvelles méthodes à la classe <xref:System.Data.Linq.DataContext> en procédant comme pour l'ajout de toute autre méthode destinée à étendre une classe.Toutefois, à propos des méthodes <xref:System.Data.Linq.DataContext> dans le contexte du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], il s'agit des méthodes <xref:System.Data.Linq.DataContext> qui mappent aux procédures stockées et aux fonctions.  
  
> [!NOTE]
>  Dans [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], les procédures stockées et fonctions sont contrôlées de la même façon et mappent aux classes d'entité en utilisant le même <xref:System.Data.Linq.StoredProcedureAttribute>.Dans le contexte [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], les méthodes <xref:System.Data.Linq.DataContext> qui mappent aux procédures stockées, sont les mêmes que celles qui mappent aux fonctions.  
  
## Volet de méthodes  
 Les méthodes <xref:System.Data.Linq.DataContext> qui mappent aux procédures stockées et aux fonctions sont affichées dans le volet de méthodes du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Le volet de méthodes est le volet situé le long du côté du volet **Entités** \(l'aire de conception principale\).Le volet de méthodes répertorie toutes les méthodes <xref:System.Data.Linq.DataContext> que vous avez créées en utilisant le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Par défaut, le volet de méthodes est vide ; faites glisser des procédures stockées ou des fonctions de l'**Explorateur de serveurs**\/**Explorateur de bases de données** sur le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] pour créer des méthodes <xref:System.Data.Linq.DataContext> et remplir le volet de méthodes.Pour plus d'informations, consultez [Procédure : créer des méthodes DataContext mappées à des procédures stockées et à des fonctions \(Concepteur O\/R\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Ouvrez et fermez le volet de méthodes en cliquant avec le bouton droit sur le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], et cliquez ensuite sur **Masquer le volet méthodes** ou **Afficher le volet méthodes** ou utilisez le raccourci clavier CTRL\+1.  
  
## Deux types de méthodes DataContext  
 Les méthodes DataContext sont les méthodes qui mappent aux procédures stockées et aux fonctions dans la base de données.Vous pouvez créer et ajouter des méthodes DataContext dans le volet de méthodes du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Il existe deux types distincts de méthodes <xref:System.Data.Linq.DataContext> : celles qui retournent un ou plusieurs jeux de résultats et celles qui ne retournent aucun jeu de résultats :  
  
-   Méthodes <xref:System.Data.Linq.DataContext> qui retournent un ou plusieurs jeux de résultats :  
  
     Créez ce type de méthode <xref:System.Data.Linq.DataContext> lorsque votre application doit juste exécuter des procédures stockées et des fonctions dans la base de données et retourner les résultats.Pour plus d'informations, consultez [Procédure : créer des méthodes DataContext mappées à des procédures stockées et à des fonctions \(Concepteur O\/R\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), <xref:System.Data.Linq.ISingleResult%271> et <xref:System.Data.Linq.IMultipleResults>.  
  
-   Méthodes <xref:System.Data.Linq.DataContext> qui ne retournent aucun jeu de résultats, par exemple celles qui effectuent des insertions, des mises à jour et des suppressions pour une classe d'entité spécifique.  
  
     Créez ce type de méthode <xref:System.Data.Linq.DataContext> lorsque votre application doit exécuter des procédures stockées au lieu d'utiliser le comportement [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] par défaut pour enregistrer des données modifiées entre une classe d'entité et la base de données.Pour plus d'informations, consultez [Procédure : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions \(Concepteur O\/R\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## Types de retour des méthodes DataContext  
 Lorsque vous faites glisser des procédures stockées et des fonctions de l'**Explorateur de serveurs**\/**Explorateur de bases de données** vers le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], le type de retour de la méthode <xref:System.Data.Linq.DataContext> générée diffère selon l'endroit où vous placez l'élément.Placer directement les éléments sur une classe d'entité existante crée une méthode <xref:System.Data.Linq.DataContext> avec le type de retour de la classe d'entité ; placer des éléments dans une zone vide du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] \(dans l'un et l'autre volet\) crée une méthode <xref:System.Data.Linq.DataContext> qui retourne un type généré automatiquement.Le type généré automatiquement possède un nom correspondant au nom de la procédure stockée ou de la fonction et des propriétés qui mappent aux champs retournés par la procédure stockée ou fonction.  
  
> [!NOTE]
>  Vous pouvez modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext> après l'avoir ajoutée au volet de méthodes.Pour inspecter ou modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext>, sélectionnez\-la et inspectez la propriété **Type de retour** dans la fenêtre **Propriétés**.Pour plus d'informations, consultez [Procédure : modifier le type de retour d'une méthode DataContext \(Concepteur O\/R\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Les objets que vous faites glisser de la base de données vers l'aire du Concepteur O\/R sont nommés automatiquement, en fonction du nom des objets dans la base de données.Lorsque vous faites glisser plusieurs fois le même objet, un numéro est ajouté à la fin du nouveau nom afin de différencier les noms.Lorsque les noms des objets de la base de données contiennent des espaces ou des caractères non pris en charge en Visual Basic ou en C\#, l'espace ou le caractère non valide est remplacé par un trait de soulignement.  
  
## Voir aussi  
 [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Procédures stockées](../Topic/Stored%20Procedures.md)   
 [Procédure : créer des méthodes DataContext mappées à des procédures stockées et à des fonctions \(Concepteur O\/R\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Procédure : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions \(Concepteur O\/R\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Procédure pas à pas : personnalisation du comportement d'insertion, de mise à jour et de suppression de classes d'entité](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Procédure pas à pas : création de classes LINQ to SQL \(Concepteur O\/R\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)