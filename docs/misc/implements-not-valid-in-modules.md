---
title: "&#39;Implements&#39; n’est pas valide dans les modules | Microsoft Docs"
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
  - "bc30231"
  - "vbc30231"
helpviewer_keywords: 
  - "BC30231"
ms.assetid: 16e6c3ea-ce89-4646-8c3f-0ef51324bc13
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Implements&#39; n’est pas valide dans les modules
Une instruction ou une clause `Implements` se trouve dans un module. Les modules ne peuvent pas implémenter des interfaces.  
  
 **ID d'erreur :** BC30231  
  
### Pour corriger cette erreur  
  
-   Supprimez l’instruction ou la clause `Implements`, ou retapez le module en tant que classe.  
  
## Voir aussi  
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [Module Statement](/dotnet/visual-basic/language-reference/statements/module-statement)