---
title: "Proc&#233;dure&#160;: modifier le type de retour d&#39;une m&#233;thode DataContext (Concepteur O/R) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure&#160;: modifier le type de retour d&#39;une m&#233;thode DataContext (Concepteur O/R)
Le type de retour d'une méthode <xref:System.Data.Linq.DataContext> \(créée selon une procédure stockée ou fonction\) diffère selon l'endroit où vous placez la procédure stockée ou la fonction dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Si vous déposez directement un élément sur une classe d'entité existante, une méthode <xref:System.Data.Linq.DataContext> ayant le type de retour de la classe d'entité est créée \(si le schéma des données a été retourné par la procédure stockée ou si la fonction correspond à la forme de la classe d'entité\).Si vous déposez un élément dans une zone vide du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], une méthode <xref:System.Data.Linq.DataContext> qui retourne un type généré automatiquement est créée.Vous pouvez modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext> après l'avoir ajoutée au volet de méthodes.Pour inspecter ou modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext>, sélectionnez\-la et cliquez sur la propriété **Type de retour** dans la fenêtre **Propriétés**.  
  
> [!NOTE]
>  Vous ne pouvez pas rétablir les méthodes <xref:System.Data.Linq.DataContext> dont le jeu de types de retour est une classe d'entité afin de retourner le type généré automatiquement via la fenêtre **Propriétés**.Pour rétablir une méthode <xref:System.Data.Linq.DataContext> afin de retourner un type généré automatiquement, vous devez faire glisser l'objet de base de données d'origine vers le Concepteur O\/R.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Pour modifier le type de retour d'une méthode DataContext du type généré automatiquement vers une classe d'entité  
  
1.  Sélectionnez la méthode <xref:System.Data.Linq.DataContext> dans le volet de méthodes.  
  
2.  Sélectionnez **Type de retour** dans la fenêtre **Propriétés**, puis sélectionnez une classe d'entité disponible dans la liste **Type de retour**.Si la classe d'entité requise ne figure pas dans la liste, ajoutez\-la ou créez\-la dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
3.  Enregistrez le fichier .dbml.  
  
### Pour modifier le type de retour d'une méthode DataContext d'une classe d'entité vers le type généré automatiquement  
  
1.  Sélectionnez la méthode <xref:System.Data.Linq.DataContext> dans le volet de méthodes et supprimez\-la.  
  
2.  Faites glisser l'objet de base de données de l'**Explorateur de serveurs**\/**Explorateur de bases de données** vers une zone vide du Concepteur 'O\/R.  
  
3.  Enregistrez le fichier .dbml.  
  
## Voir aussi  
 [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Méthodes DataContext \(Concepteur O\/R\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procédure : créer des méthodes DataContext mappées à des procédures stockées et à des fonctions \(Concepteur O\/R\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)