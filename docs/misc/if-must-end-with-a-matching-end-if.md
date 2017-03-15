---
title: "&#39;If&#39; doit se terminer par un &#39;End If&#39; correspondant | Microsoft Docs"
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
  - "bc30081"
  - "vbc30081"
helpviewer_keywords: 
  - "BC30081"
ms.assetid: e5905d59-56bb-4daf-aca5-5ff847fc62f6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;If&#39; doit se terminer par un &#39;End If&#39; correspondant
Il existe une occurrence d’instruction `If` sans instruction `End If` correspondante. Vous devez utiliser une instruction `End If` pour terminer le bloc `If`.  
  
 **ID d’erreur :** BC30081  
  
### Pour corriger cette erreur  
  
1.  Si ce bloc `If` fait partie d’un ensemble de blocs `If` imbriqués, Vérifiez que chaque bloc se termine correctement.  
  
2.  Ajoutez une instruction `End If` à la fin du bloc `If`.  
  
## Voir aussi  
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)