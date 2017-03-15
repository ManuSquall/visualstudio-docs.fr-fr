---
title: "&#39;Exit Select&#39; ne peut appara&#238;tre qu’&#224; l’int&#233;rieur d’une instruction &#39;Select&#39; | Microsoft Docs"
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
  - "vbc30099"
  - "bc30099"
helpviewer_keywords: 
  - "BC30099"
ms.assetid: 37c65fc8-6ad9-456a-80b8-66288c62ef24
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Select&#39; ne peut appara&#238;tre qu’&#224; l’int&#233;rieur d’une instruction &#39;Select&#39;
Une instruction `Exit Select` se trouve en dehors d’un bloc `Select`.`Exit Select` est valide uniquement entre une instruction `Select` ou `Select Case` et une instruction `End Select` correspondante.  
  
 **ID d’erreur :** BC30099  
  
### Pour corriger cette erreur  
  
1.  Assurez\-vous qu’une instruction `Select` ou `Select Case` valide précède `Exit Select` et qu’une instruction `End Select` valide se trouve après.  
  
2.  Vérifiez que les autres structures de contrôle du bloc `Select` ont correctement été terminées.  
  
## Voir aussi  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)