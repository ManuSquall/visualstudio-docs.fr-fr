---
title: "Impossible de supprimer la propri&#233;t&#233; &lt;nom de la propri&#233;t&#233;&gt; car elle participe &#224; l&#39;association &lt;nom de l&#39;association&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Impossible de supprimer la propri&#233;t&#233; &lt;nom de la propri&#233;t&#233;&gt; car elle participe &#224; l&#39;association &lt;nom de l&#39;association&gt;
La propriété sélectionnée est définie comme **Propriété d'association** pour l'association de classes indiquée dans le message d'erreur.Les propriétés ne peuvent pas être supprimées si elles participent à une association entre des classes de données.  
  
 Affectez à **Propriété d'association** une propriété différente de la classe de données pour permettre la suppression de la propriété désirée.  
  
### Pour corriger cette erreur  
  
1.  Dans le Concepteur O\/R, sélectionnez la ligne d'association qui connecte les classes de données indiquées dans le message d'erreur.  
  
2.  Double\-cliquez sur la ligne pour ouvrir la boîte de dialogue **Éditeur d'associations**.  
  
3.  Supprimez la propriété des **Propriétés d'association**.  
  
4.  Essayez une nouvelle fois de supprimer la propriété.  
  
## Voir aussi  
 [Vue d'ensemble du Concepteur O\/R](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Procédure : créer une association \(relation\) entre des classes LINQ to SQL \(Concepteur O\/R\)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Procédure pas à pas : création de classes LINQ to SQL \(Concepteur O\/R\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)