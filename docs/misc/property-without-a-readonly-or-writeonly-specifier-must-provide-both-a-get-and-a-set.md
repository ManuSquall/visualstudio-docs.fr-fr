---
title: "Une propri&#233;t&#233; sans sp&#233;cificateur &#39;ReadOnly&#39; ou &#39;WriteOnly&#39; doit fournir un &#39;Get&#39; et un &#39;Set&#39; | Microsoft Docs"
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
  - "bc30124"
  - "vbc30124"
helpviewer_keywords: 
  - "BC30124"
ms.assetid: b24fc997-9a6b-44d1-b712-dab498a6fc72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une propri&#233;t&#233; sans sp&#233;cificateur &#39;ReadOnly&#39; ou &#39;WriteOnly&#39; doit fournir un &#39;Get&#39; et un &#39;Set&#39;
Si une propriété n’est pas déclarée comme `ReadOnly` ou `WriteOnly`, elle doit fournir des procédures pour lire et écrire sa valeur.  
  
 **ID d’erreur :** BC30124  
  
### Pour corriger cette erreur  
  
1.  Veillez à inclure une procédure `Get` et une procédure `Set` entre l’instruction `Property` et l’instruction `End Property`.  
  
2.  Vérifiez que les autres procédures de la déclaration `Property` se terminent correctement.  
  
## Voir aussi  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)