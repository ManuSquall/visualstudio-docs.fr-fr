---
title: "&#39;Select Case&#39; doit se terminer par un &#39;End Select&#39; correspondant | Microsoft Docs"
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
  - "vbc30095"
  - "bc30095"
helpviewer_keywords: 
  - "BC30095"
ms.assetid: f0809aa5-e6c9-43c9-9664-4ff02825c3d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Select Case&#39; doit se terminer par un &#39;End Select&#39; correspondant
Une instruction `Select` ou `Select Case` se produit sans instruction `End Select` correspondante. Vous devez utiliser une instruction `End Select` pour terminer le bloc `Select`.  
  
 **ID d’erreur :** BC30095  
  
### Pour corriger cette erreur  
  
1.  Si ce bloc `Select` fait partie d’un ensemble de blocs `Select` imbriqués, vérifiez que chaque bloc est correctement terminé.  
  
2.  Ajoutez une instruction `End Select` à la fin du bloc `Select`.  
  
## Voir aussi  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)