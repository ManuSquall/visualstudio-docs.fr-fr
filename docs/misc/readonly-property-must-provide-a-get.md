---
title: "Une propri&#233;t&#233; &#39;ReadOnly&#39; doit fournir un &#39;Get&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30126"
  - "vbc30126"
helpviewer_keywords: 
  - "BC30126"
ms.assetid: a522c39e-1f11-45c8-a00b-3546c842909a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une propri&#233;t&#233; &#39;ReadOnly&#39; doit fournir un &#39;Get&#39;
Si une propriété est déclarée comme `ReadOnly`, elle doit fournir une procédure permettant de lire sa valeur.  
  
 **ID d'erreur :** BC30126  
  
### Pour corriger cette erreur  
  
1.  Veillez à inclure une procédure `Get` entre l’instruction `Property`et l’instruction `End Property`.  
  
2.  Vérifiez que les autres procédures de la déclaration `Property` se terminent correctement.  
  
## Voir aussi  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)