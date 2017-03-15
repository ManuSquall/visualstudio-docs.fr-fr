---
title: "Les structures ne peuvent pas d&#233;clarer un &#39;Sub New&#39; non partag&#233; sans param&#232;tre | Microsoft Docs"
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
  - "vbc30629"
  - "bc30629"
helpviewer_keywords: 
  - "BC30629"
ms.assetid: f4298ef7-85b1-4543-b764-4c3abda84baa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les structures ne peuvent pas d&#233;clarer un &#39;Sub New&#39; non partag&#233; sans param&#232;tre
Les constructeurs `Sub New` déclarés dans des structures doivent accepter des arguments ou être déclarés avec le modificateur `Shared`.  
  
 **ID d’erreur :** BC30629  
  
### Pour corriger cette erreur  
  
-   Modifiez le constructeur `Sub New` pour qu’il accepte des arguments.  
  
-   Appliquez le modificateur `Shared` pour que le constructeur soit partagé.  
  
## Voir aussi  
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [Structures](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)