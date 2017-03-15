---
title: "&#39;Assembly&#39; ou &#39;Module&#39; attendu | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32015"
  - "bc32015"
helpviewer_keywords: 
  - "BC32015"
ms.assetid: 6e62fe8d-a875-4995-b6b2-443e75c65e85
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Assembly&#39; ou &#39;Module&#39; attendu
Un attribut global est spécifié sans indiquer s’il s’applique à la totalité de l’assembly ou uniquement au module actuel. Les attributs globaux doivent spécifier `Assembly` ou `Module`.  
  
 Un attribut global est un attribut qui apparaît tout seul sur une ligne source, plutôt qu’appliqué à la déclaration d’un élément de programmation particulier.  
  
 **ID d’erreur :** BC32015  
  
### Pour corriger cette erreur  
  
1.  Si vous voulez que l’attribut soit global, ajoutez le mot clé `Assembly` ou `Module` au début du bloc d’attributs, suivi d’un deux\-points \(:\).  
  
2.  Si vous ne voulez pas que l’attribut soit global, supprimez le bloc d’attributs ou déplacez\-le vers une déclaration d’élément de programmation.  
  
## Voir aussi  
 [Assembly](/dotnet/visual-basic/language-reference/modifiers/assembly)   
 [Module \<keyword\>](../Topic/Module%20%3Ckeyword%3E%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [NOT IN BUILD : Attributs globaux en Visual Basic](http://msdn.microsoft.com/fr-fr/253a32d8-1531-4504-b687-088554ab71d2)