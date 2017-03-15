---
title: "Impossible de supprimer la propri&#233;t&#233; &lt;nom de la propri&#233;t&#233;&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# Impossible de supprimer la propri&#233;t&#233; &lt;nom de la propri&#233;t&#233;&gt;
La propriété \<nom de la propriété\>ne peut pas être supprimée parce qu'elle est définie en tant que propriété de discriminateur pour l'héritage entre \<nom de la classe\> et \<nom de la classe\>  
  
 La propriété sélectionnée est définie comme **Propriété de discriminateur** pour l'héritage entre les classes indiquées dans le message d'erreur.Les propriétés ne peuvent pas être supprimées si elles participent à la configuration d'héritage entre des classes de données.  
  
 Affectez à **Propriété de discriminateur** une propriété différente de la classe de données pour permettre la suppression de la propriété désirée.  
  
### Pour corriger cette erreur  
  
1.  Dans le Concepteur O\/R, sélectionnez la ligne d'héritage qui connecte les classes de données indiquées dans le message d'erreur.  
  
2.  Affectez à **Propriété de discriminateur**  une propriété différente.  
  
3.  Essayez une nouvelle fois de supprimer la propriété.  
  
## Voir aussi  
 [Procédure : configurer l'héritage à l'aide du Concepteur O\/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Héritage de classes de données \(Concepteur O\/R\)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Procédure pas à pas : création de classes LINQ to SQL à l'aide de l'héritage à table unique \(Concepteur O\/R\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)