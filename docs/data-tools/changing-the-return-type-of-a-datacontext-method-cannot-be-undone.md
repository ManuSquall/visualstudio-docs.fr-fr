---
title: "Impossible d&#39;annuler la modification du type de retour d&#39;une m&#233;thode DataContext | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Impossible d&#39;annuler la modification du type de retour d&#39;une m&#233;thode DataContext
Impossible d'annuler la modification du type de retour d'une méthode DataContext.Pour revenir au type généré automatiquement, vous devez déplacer à nouveau l'élément de l'Explorateur de serveurs\/Explorateur de bases de données vers le Concepteur O\/R.Êtes\-vous sûr de vouloir modifier le type de retour ?  
  
 Le type de retour d'une méthode <xref:System.Data.Linq.DataContext> diffère selon l'endroit où vous placez l'élément dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Si vous placez directement un élément dans une classe d'entité existante, une méthode <xref:System.Data.Linq.DataContext> qui a le type de retour de la classe d'entité est créée.Si vous déposez un élément dans une zone vide du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], une méthode <xref:System.Data.Linq.DataContext> qui retourne un type généré automatiquement est créée.Vous pouvez modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext> après l'avoir ajoutée au volet de méthodes.Pour inspecter ou modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext>, sélectionnez\-la et cliquez sur la propriété **Type de retour** dans la fenêtre **Propriétés**.  
  
### Pour modifier le type de retour d'un DataContext  
  
-   Cliquez sur **Oui**.  
  
### Pour sortir de la boîte de message et laisser le type de retour inchangé  
  
-   Cliquez sur **Non**.  
  
### Pour rétablir le type de retour d'origine après l'avoir modifié  
  
1.  Sélectionnez la méthode <xref:System.Data.Linq.DataContext> dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] et supprimez\-la.  
  
2.  Localisez l'élément dans l'**Explorateur de serveurs\/Explorateur de bases de données** et faites\-le glisser vers le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Une méthode <xref:System.Data.Linq.DataContext> est créée avec le type de retour par défaut d'origine.  
  
## Voir aussi  
 [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Méthodes DataContext \(Concepteur O\/R\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procédure : créer des méthodes DataContext mappées à des procédures stockées et à des fonctions \(Concepteur O\/R\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)