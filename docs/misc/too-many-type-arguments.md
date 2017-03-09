---
title: "Arguments de type trop nombreux | Microsoft Docs"
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
  - "vbc36579"
  - "bc36579"
helpviewer_keywords: 
  - "BC36579"
ms.assetid: f59617b2-ca66-45c6-baaa-3c8bdf7f9a55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Arguments de type trop nombreux
Une méthode générique a été appelée avec plus d’arguments de type qu’il n’y a de paramètres de type.  
  
 Quand vous appelez une méthode générique, vous devez fournir autant d’arguments de type qu’il y a de paramètres de type définis par cette méthode.  
  
 **ID d’erreur :** BC36579  
  
### Pour corriger cette erreur  
  
-   Supprimez des arguments de type de votre liste d’arguments de type pour qu’il y en un pour chaque paramètre de type de la méthode générique que vous appelez.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)