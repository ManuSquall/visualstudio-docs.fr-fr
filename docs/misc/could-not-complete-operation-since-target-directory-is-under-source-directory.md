---
title: "Impossible d’achever l’op&#233;ration, car le r&#233;pertoire cible se situe sous le r&#233;pertoire source | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrIO_CyclicOperation"
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’achever l’op&#233;ration, car le r&#233;pertoire cible se situe sous le r&#233;pertoire source
Une opération cyclique a échoué. Les opérations cycliques se répètent et, par conséquent, ne peuvent pas s’achever. Par exemple, l’objet A peut essayer d’hériter de l’objet B qui hérite, à son tour, de l’objet A.  
  
### Pour corriger cette erreur  
  
-   Lors d’un héritage, vérifiez qu’il n’existe aucune référence cyclique.  
  
## Voir aussi  
 [Error Types](/dotnet/visual-basic/programming-guide/language-features/error-types)   
 [Debugging Basics: Breakpoints](http://msdn.microsoft.com/fr-fr/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)