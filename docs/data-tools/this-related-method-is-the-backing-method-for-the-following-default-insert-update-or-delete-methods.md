---
title: "Cette m&#233;thode associ&#233;e est la m&#233;thode de stockage pour les m&#233;thodes par d&#233;faut d&#39;insertion, de mise &#224; jour ou de suppression suivantes | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Cette m&#233;thode associ&#233;e est la m&#233;thode de stockage pour les m&#233;thodes par d&#233;faut d&#39;insertion, de mise &#224; jour ou de suppression suivantes
Cette méthode associée est la méthode de stockage pour les méthodes par défaut d'insertion, de mise à jour ou de suppression suivantes.Si vous la supprimez, ces méthodes seront aussi supprimées.Voulez\-vous continuer ?  
  
 La méthode `DataContext` sélectionnée est actuellement utilisée comme l'une des méthodes d'insertion, de mise à jour et de suppression pour l'une des classes d'entité dans le Concepteur O\/R.La suppression de la méthode sélectionnée provoquera, pour la classe d'entité qui l'utilisait, le retour au comportement au moment de l'exécution par défaut pour les méthodes d'insertion, de mise à jour et de suppression lors d'une mise à jour.  
  
### Pour supprimer la méthode sélectionnée et obliger la classe d'entité à utiliser des mises à jour au moment de l'exécution  
  
-   Cliquez sur **Oui**.  
  
     La méthode sélectionnée est supprimée et toutes les classes qui ont utilisé cette méthode pour substituer le comportement de mise à jour sont réinitialisées à la valeur par défaut du comportement au moment de l'exécution par défaut LINQ to SQL.  
  
### Pour fermer le message en laissant la méthode sélectionnée inchangée  
  
-   Cliquez sur **Non**.  
  
     La boîte de message se ferme et aucune modification n'est apportée.  
  
## Voir aussi  
 [Méthodes DataContext \(Concepteur O\/R\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procédure : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions \(Concepteur O\/R\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Vue d'ensemble du Concepteur O\/R](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)