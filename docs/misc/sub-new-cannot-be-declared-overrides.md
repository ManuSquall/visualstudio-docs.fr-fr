---
title: "&#39;Sub New&#39; ne peut pas &#234;tre d&#233;clar&#233; &#39;Overrides&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30283"
  - "bc30283"
helpviewer_keywords: 
  - "BC30283"
ms.assetid: 0e71cdcb-b62e-4a36-8829-83de5c453c74
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; ne peut pas &#234;tre d&#233;clar&#233; &#39;Overrides&#39;
Un constructeur indique qu’il substitue un constructeur hérité. Les constructeurs ne peuvent pas être substitués.  
  
 **ID d’erreur :** BC30283  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Overrides` de la déclaration `Sub`.  
  
## Voir aussi  
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [NOT IN BUILD : Utilisation des constructeurs et des destructeurs](http://msdn.microsoft.com/fr-fr/548eebe1-86c4-4377-b2f5-447cb8be3d90)