---
title: "&#39;Exit Operator&#39; n’est pas valide. Utilisez &#39;Return&#39; pour quitter un op&#233;rateur | Microsoft Docs"
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
  - "bc33008"
  - "vbc33008"
helpviewer_keywords: 
  - "BC33008"
ms.assetid: 8c44456b-8fd2-4168-ad8c-b6da129242ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Operator&#39; n’est pas valide. Utilisez &#39;Return&#39; pour quitter un op&#233;rateur
Une instruction `Exit Operator` apparaît dans une procédure `Operator`.  
  
 Vous devez utiliser un [Return Statement](/dotnet/visual-basic/language-reference/statements/return-statement) pour quitter une procédure `Operator`.[Exit Statement](/dotnet/visual-basic/language-reference/statements/exit-statement) n’accepte pas le mot clé `Operator` et l’instruction `End Operator` ne retourne pas le contrôle au code appelant.  
  
 **ID d’erreur :** BC33008  
  
### Pour corriger cette erreur  
  
-   Remplacez l’instruction `Exit Operator` par une instruction `Return`.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)