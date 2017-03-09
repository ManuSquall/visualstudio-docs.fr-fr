---
title: "Un modificateur &#39;Custom&#39; ne peut &#234;tre utilis&#233; qu’imm&#233;diatement avant une d&#233;claration &#39;Event&#39; | Microsoft Docs"
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
  - "vbc31140"
  - "bc31140"
helpviewer_keywords: 
  - "BC31140"
ms.assetid: e516fb5d-b11b-483b-92d0-ac7064d1841d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Un modificateur &#39;Custom&#39; ne peut &#234;tre utilis&#233; qu’imm&#233;diatement avant une d&#233;claration &#39;Event&#39;
Le mot clé `Custom` doit précéder uniquement le mot clé `Event` dans une déclaration d’événement personnalisé.  
  
 **ID d’erreur :** BC31140  
  
### Pour corriger cette erreur  
  
-   Placez le mot clé `Custom` avant le mot clé `Event`.  
  
     \- ou \-  
  
-   Supprimez le mot clé `Custom`.  
  
## Voir aussi  
 [Custom \- delete](http://msdn.microsoft.com/fr-fr/dc62be07-c896-4866-a533-982a661d143f)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)