---
title: "&#39;Exit For&#39; ne peut appara&#238;tre qu’&#224; l’int&#233;rieur d’une instruction &#39;For&#39; | Microsoft Docs"
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
  - "bc30096"
  - "vbc30096"
helpviewer_keywords: 
  - "BC30096"
ms.assetid: 1062a329-9364-4234-9175-4c70a51cb7ae
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit For&#39; ne peut appara&#238;tre qu’&#224; l’int&#233;rieur d’une instruction &#39;For&#39;
Une instruction `Exit For` se trouve en dehors d’une boucle `For`.`Exit For` est valide uniquement entre une instruction `For` ou `For Each` et une instruction `Next` correspondante.  
  
 **ID d’erreur :** BC30096  
  
### Pour corriger cette erreur  
  
1.  Vérifiez qu’une instruction `For` ou `For Each` valide précède `Exit For` et qu’une instruction `Next` valide le suit.  
  
2.  Vérifiez que les autres structures de contrôle dans la boucle `For` sont terminées correctement.  
  
## Voir aussi  
 [For...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [For Each...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)