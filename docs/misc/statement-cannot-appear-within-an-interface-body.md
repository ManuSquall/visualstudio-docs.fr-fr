---
title: "L’instruction ne peut pas appara&#238;tre dans le corps d’une interface | Microsoft Docs"
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
  - "vbc30603"
  - "BC30603"
helpviewer_keywords: 
  - "BC30603"
ms.assetid: 3aef29d6-eadf-4f1f-b214-dfeae5e51c4f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’instruction ne peut pas appara&#238;tre dans le corps d’une interface
La déclaration d’un membre d’interface comprend une instruction qui arrête le membre. L’instruction est au format suivant : `End` *nom\_membre*.  
  
 Une interface définit uniquement la signature de ses membres. Les procédures et les propriétés définies d’une interface ont uniquement leur ligne initiale, dans laquelle sont spécifiés le nom et la signature. Vous ne pouvez pas inclure de code, de déclarations internes ou d’instructions `End Function`, `End Property` ou `End Sub` dans l’interface.  
  
 **ID d’erreur :** BC30603  
  
### Pour corriger cette erreur  
  
-   Supprimez l’instruction `End` *nom\_membre* de la définition d’interface.  
  
## Voir aussi  
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)