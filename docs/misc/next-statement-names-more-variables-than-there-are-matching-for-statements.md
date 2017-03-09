---
title: "L’instruction &#39;Next&#39; nomme plus de variables qu’il n’existe d’instructions &#39;For&#39; correspondantes | Microsoft Docs"
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
  - "bc32037"
  - "vbc32037"
helpviewer_keywords: 
  - "BC32037"
ms.assetid: 7c97d835-1043-40ec-a645-63a053f5f916
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’instruction &#39;Next&#39; nomme plus de variables qu’il n’existe d’instructions &#39;For&#39; correspondantes
Les boucles imbriquées sont terminées avec une seule instruction `Next` qui spécifie plus de variables de boucle qu’il n’y en a dans l’imbrication, comme dans l’exemple suivant :  
  
```  
For I = 1 To 10 For J = 1 To 5 ' ... Next J, I, K   ' Next J, I is valid, but there is no loop on K.  
```  
  
 **ID d’erreur :** BC32037  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que l’instruction `Next` spécifie toutes les variables de boucle imbriquées dans l’ordre inverse de leur initiation.  
  
2.  Supprimez les variables superflues de l’instruction `Next`.  
  
## Voir aussi  
 [For...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-next-statement)