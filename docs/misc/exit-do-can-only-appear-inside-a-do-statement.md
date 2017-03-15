---
title: "&#39;Exit Do&#39; ne peut appara&#238;tre qu’&#224; l’int&#233;rieur d’une instruction &#39;Do&#39; | Microsoft Docs"
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
  - "bc30089"
  - "vbc30089"
helpviewer_keywords: 
  - "BC30089"
ms.assetid: 0e1d0b35-e42b-4b90-b8a2-91fd6ef44f06
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Do&#39; ne peut appara&#238;tre qu’&#224; l’int&#233;rieur d’une instruction &#39;Do&#39;
Une instruction `Exit Do` se trouve en dehors d’une boucle `Do`.`Exit Do` n’est valide qu’entre une instruction `Do` et une instruction `Loop` correspondante.  
  
 **ID d’erreur :** BC30089  
  
### Pour corriger cette erreur  
  
1.  Vérifiez qu’une instruction `Do` valide précède `Exit Do` et qu’une instruction `Loop` valide le suit.  
  
2.  Vérifiez que les autres structures de contrôle de la boucle `Do` sont terminées correctement.  
  
## Voir aussi  
 [Do...Loop Statement](/dotnet/visual-basic/language-reference/statements/do-loop-statement)