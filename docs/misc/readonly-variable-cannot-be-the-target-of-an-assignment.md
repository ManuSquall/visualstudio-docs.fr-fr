---
title: "Une variable &#39;ReadOnly&#39; ne peut pas &#234;tre la cible d’une assignation | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30064"
  - "bc30064"
helpviewer_keywords: 
  - "BC30064"
ms.assetid: 17e0751d-4c22-40b2-bb07-cb5c845dbc30
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une variable &#39;ReadOnly&#39; ne peut pas &#234;tre la cible d’une assignation
Une propriété `ReadOnly` a été trouvée dans un contexte qui lui assigne une valeur. Seules les variables, les propriétés et les éléments de tableau accessibles en écriture peuvent recevoir des valeurs durant l’exécution.  
  
 **ID d’erreur :** BC30064  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `ReadOnly` de l’instruction `Dim` qui déclare la variable, ou supprimez l’instruction qui lui assigne une valeur.  
  
## Voir aussi  
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)