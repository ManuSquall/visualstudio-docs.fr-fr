---
title: "Proc&#233;dure&#160;: cr&#233;er des m&#233;thodes DataContext mapp&#233;es &#224; des proc&#233;dures stock&#233;es et &#224; des fonctions (Concepteur O/R) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure&#160;: cr&#233;er des m&#233;thodes DataContext mapp&#233;es &#224; des proc&#233;dures stock&#233;es et &#224; des fonctions (Concepteur O/R)
Les procédures stockées et fonctions peuvent être ajoutées au [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] comme méthodes <xref:System.Data.Linq.DataContext>.En appelant la méthode pour passer les paramètres requis, la procédure stockée ou fonction est exécutée sur la base de données et retourne les données dans le type de retour de la méthode <xref:System.Data.Linq.DataContext>.Pour plus d'informations sur les méthodes <xref:System.Data.Linq.DataContext>, consultez [Méthodes DataContext \(Concepteur O\/R\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Les procédures stockées peuvent également être utilisées pour substituer le comportement au moment de l'exécution par défaut de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] qui effectue des insertions, des mises à jour et des suppressions lorsque les modifications sont enregistrées des classes d'entité vers une base de données.Pour plus d'informations, consultez [Procédure : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions \(Concepteur O\/R\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## Création de méthodes DataContext  
 Vous pouvez créer des méthodes <xref:System.Data.Linq.DataContext> en faisant glisser des procédures stockées ou des fonctions de l'**Explorateur de serveurs\/Explorateur de bases de données** vers le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
> [!NOTE]
>  Le type de retour de la méthode <xref:System.Data.Linq.DataContext> générée diffère selon l'endroit où vous placez la procédure stockée ou fonction dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Le déplacement direct des éléments vers une classe d'entité existante crée une méthode <xref:System.Data.Linq.DataContext> avec le type de retour de la classe d'entité.Le déplacement d'éléments vers une zone vide dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] crée une méthode <xref:System.Data.Linq.DataContext> qui retourne un type généré automatiquement.Vous pouvez modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext> après l'avoir ajoutée au volet de méthodes.Pour inspecter ou modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext>, sélectionnez\-la et inspectez la propriété **Type de retour** dans la fenêtre **Propriétés**.Pour plus d'informations, consultez [Procédure : modifier le type de retour d'une méthode DataContext \(Concepteur O\/R\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Pour créer des méthodes DataContext qui retournent automatiquement les types générés  
  
1.  Dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**, développez le nœud **Procédures stockées** de la base de données avec laquelle vous travaillez.  
  
2.  Localisez la procédure stockée requise et faites\-la glisser vers une zone vide dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     La méthode <xref:System.Data.Linq.DataContext> est créée avec un type de retour généré automatiquement et apparaît dans le volet **Méthodes**.  
  
#### Pour créer des méthodes DataContext qui ont le type de retour d'une classe d'entité  
  
1.  Dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**, développez le nœud **Procédures stockées** de la base de données avec laquelle vous travaillez.  
  
2.  Localisez la procédure stockée requise et faites\-la glisser sur une classe d'entité existante dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     La méthode <xref:System.Data.Linq.DataContext> est créée avec le type de retour de la classe d'entité sélectionnée et apparaît dans le volet **Méthodes**.  
  
> [!NOTE]
>  Pour plus d'informations sur la modification du type de retour des méthodes <xref:System.Data.Linq.DataContext> existantes, consultez [Procédure : modifier le type de retour d'une méthode DataContext \(Concepteur O\/R\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## Voir aussi  
 [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Méthodes DataContext \(Concepteur O\/R\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procédure pas à pas : création de classes LINQ to SQL \(Concepteur O\/R\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Comment : écrire des requêtes LINQ en C\#](../Topic/How%20to:%20Write%20LINQ%20Queries%20in%20C%23.md)