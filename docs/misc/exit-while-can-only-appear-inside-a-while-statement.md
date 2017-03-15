---
title: "&#39;Exit While&#39; ne peut appara&#238;tre qu’&#224; l’int&#233;rieur d’une instruction &#39;While&#39; | Microsoft Docs"
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
  - "vbc30097"
  - "bc30097"
helpviewer_keywords: 
  - "BC30097"
ms.assetid: cf0a3e09-5252-4198-bb27-c103c98d9f19
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit While&#39; ne peut appara&#238;tre qu’&#224; l’int&#233;rieur d’une instruction &#39;While&#39;
Une instruction `Exit While` se trouve en dehors d’un bloc `While`.`Exit While` n’est valide qu’entre une instruction `While` et une instruction `End While`.  
  
 **ID d’erreur :** BC30097  
  
### Pour corriger cette erreur  
  
1.  Assurez\-vous qu’une instruction `While` valide précède `Exit While` et qu’une instruction `End While` valide se trouve après celle\-ci.  
  
2.  Vérifiez que les autres structures de contrôle du bloc `While` ont été correctement terminées.  
  
## Voir aussi  
 [While...End While Statement](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)