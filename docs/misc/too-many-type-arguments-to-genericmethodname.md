---
title: "Arguments de type trop nombreux dans &#39;&lt;nom_m&#233;thode_g&#233;n&#233;rique&gt;&#39; | Microsoft Docs"
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
  - "bc32043"
  - "vbc32043"
helpviewer_keywords: 
  - "BC32043"
ms.assetid: c4d8f67a-4317-461a-9446-6717cfa1d888
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Arguments de type trop nombreux dans &#39;&lt;nom_m&#233;thode_g&#233;n&#233;rique&gt;&#39;
Une méthode générique a été appelée avec plus d’arguments de type qu’il n’y a de paramètres de type.  
  
 Quand vous appelez une méthode générique, vous devez fournir un argument de type pour chaque paramètre de type défini par cette méthode.  
  
 **ID d’erreur :** BC32043  
  
### Pour corriger cette erreur  
  
-   Supprimez des arguments de type de votre liste d’arguments de type pour qu’il y en ait un pour chaque paramètre de type dans la méthode générique que vous appelez.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)