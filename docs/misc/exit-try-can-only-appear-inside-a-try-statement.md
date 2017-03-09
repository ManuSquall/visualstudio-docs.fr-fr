---
title: "&#39;Exit Try&#39; ne peut appara&#238;tre qu’&#224; l’int&#233;rieur d’une instruction &#39;Try&#39; | Microsoft Docs"
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
  - "vbc30393"
  - "bc30393"
helpviewer_keywords: 
  - "BC30393"
ms.assetid: b8651df3-a32f-478c-a6d8-aa0ef584155f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Try&#39; ne peut appara&#238;tre qu’&#224; l’int&#233;rieur d’une instruction &#39;Try&#39;
`Exit Try` ne peut figurer qu’à l’intérieur d’une instruction de bloc `Try`. Soit vous avez une instruction `Exit Try` redondante, soit votre instruction `Exit Try` apparaît en dehors des limites de son bloc `Try` correspondant.  
  
 **ID d’erreur :** BC30393  
  
### Pour corriger cette erreur  
  
1.  Recherchez et supprimez l’instruction `Exit Try` inutile.  
  
2.  Déplacez l’instruction `Exit Try`à l’emplacement approprié dans votre code.  
  
## Voir aussi  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Vue d’ensemble de la gestion structurée des exceptions pour Visual Basic](http://msdn.microsoft.com/fr-fr/bb81af80-a735-4873-9711-6151a48e418a)