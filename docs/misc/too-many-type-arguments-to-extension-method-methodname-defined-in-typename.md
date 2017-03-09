---
title: "Arguments de type trop nombreux dans la m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finie dans &#39;&lt;nom_type&gt;&#39; | Microsoft Docs"
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
  - "bc36591"
  - "vbc36591"
helpviewer_keywords: 
  - "BC36591"
ms.assetid: 504c9b1f-f511-4198-8970-136d1a1bdafe
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Arguments de type trop nombreux dans la m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finie dans &#39;&lt;nom_type&gt;&#39;
Une méthode d’extension générique a été appelée avec plus d’arguments de type qu’il n’y a de paramètres de type.  
  
 Quand vous appelez une méthode générique, vous devez fournir autant d’arguments de type qu’il y a de paramètres de type définis par cette méthode.  
  
 **ID d’erreur :** BC36591  
  
### Pour corriger cette erreur  
  
-   Supprimez des arguments de type de votre liste d’arguments de type pour qu’il y en ait un pour chaque paramètre de type défini par la méthode générique que vous appelez.  
  
## Voir aussi  
 [méthodes d'extension.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)