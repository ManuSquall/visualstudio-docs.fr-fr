---
title: "L’instruction &#39;Throw&#39; ne peut pas omettre l’op&#233;rande en dehors d’une instruction &#39;Catch&#39; ou dans une instruction &#39;Finally&#39; | Microsoft Docs"
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
  - "vbc30666"
  - "bc30666"
helpviewer_keywords: 
  - "BC30666"
ms.assetid: a208a6ea-0e36-4bf1-8984-4de1a0e38a2a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’instruction &#39;Throw&#39; ne peut pas omettre l’op&#233;rande en dehors d’une instruction &#39;Catch&#39; ou dans une instruction &#39;Finally&#39;
Les instructions `Throw` situées en dehors de l’instruction `Catch` doivent fournir le nom d’un objet exception.  
  
 **ID d’erreur :** BC30666  
  
### Pour corriger cette erreur  
  
1.  Spécifiez le nom d’un objet d’exception dérivé de `System.Exception`.  
  
2.  Restructurez votre code pour que l’instruction `Throw` se trouve dans un bloc `Catch`.  
  
## Voir aussi  
 [Throw Statement](/dotnet/visual-basic/language-reference/statements/throw-statement)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Classe d’exception en Visual Basic](http://msdn.microsoft.com/fr-fr/9aac396f-34ca-4afb-8e6c-e523cb690ba9)   
 [Gestion des exceptions et des erreurs en Visual Basic](http://msdn.microsoft.com/fr-fr/3e351e73-cf23-40ab-8b60-05794160529e)