---
title: "&#39;Finally&#39; ne peut pas figurer en dehors d’une instruction&#160;&#39;Try&#39;. | Microsoft Docs"
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
  - "vbc30382"
  - "bc30382"
helpviewer_keywords: 
  - "BC30382"
ms.assetid: 0314d8d2-18bc-4bbd-858c-0a18408b52fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Finally&#39; ne peut pas figurer en dehors d’une instruction&#160;&#39;Try&#39;.
L’instruction `Finally` permet de terminer un bloc `Try...Catch...Finally` ; par conséquent, elle ne peut figurer qu’une seule fois à la fin du bloc. Soit vous avez une instruction `Finally` inutile, soit votre instruction`Finally` apparaît en dehors des limites de son bloc `Try` correspondant.  
  
 **ID d’erreur :** BC30382  
  
### Pour corriger cette erreur  
  
1.  Recherchez et supprimez l’instruction `Finally`**inutile**.  
  
2.  Déplacez l’instruction `Finally` vers l’emplacement approprié dans votre code.  
  
## Voir aussi  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Vue d’ensemble de la gestion structurée des exceptions pour Visual Basic](http://msdn.microsoft.com/fr-fr/bb81af80-a735-4873-9711-6151a48e418a)