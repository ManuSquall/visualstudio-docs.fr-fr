---
title: "L’argument de type &#39;&lt;nom_argument_type&gt;&#39; n’h&#233;rite pas ou n’impl&#233;mente pas le type de contrainte &#39;&lt;nom_param&#232;tre_type&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32044"
  - "vbc32044"
helpviewer_keywords: 
  - "BC32044"
ms.assetid: be91f648-c07d-4991-8ed1-28b1327619c4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’argument de type &#39;&lt;nom_argument_type&gt;&#39; n’h&#233;rite pas ou n’impl&#233;mente pas le type de contrainte &#39;&lt;nom_param&#232;tre_type&gt;&#39;
Un argument de type fourni à un type générique ne satisfait pas la contrainte d’héritage ou d’implémentation sur son paramètre de type correspondant.  
  
 Une liste de contraintes impose des exigences sur l’argument de type passé au paramètre de type. Les exigences possibles sont les suivantes :  
  
-   L’argument de type doit implémenter une ou plusieurs interfaces  
  
-   L’argument de type doit hériter d’une classe au plus  
  
 Vous pouvez combiner les exigences précédentes pour un seul paramètre de type.[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne peut pas construire le type, sauf si le code fournit des arguments de type qui satisfont chaque contrainte sur chaque paramètre de type défini sur le type générique.  
  
 **ID d’erreur :** BC32044  
  
### Pour corriger cette erreur  
  
-   Sélectionnez un argument de type d’un type qui implémente chaque interface spécifiée pour le paramètre de type et qui hérite de la classe spécifiée s’il en existe une.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Comment : utiliser une classe générique](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)