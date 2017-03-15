---
title: "&#39;Catch&#39; ne peut pas intercepter le type &#39;&lt;nom_type&gt;&#39;, car il ne s’agit pas de &#39;System.Exception&#39; ni d’une classe qui h&#233;rite de &#39;System.Exception&#39;. | Microsoft Docs"
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
  - "vbc30392"
  - "bc30392"
helpviewer_keywords: 
  - "BC30392"
ms.assetid: 1d513d1d-38f5-4b4e-95bb-9f1209553803
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Catch&#39; ne peut pas intercepter le type &#39;&lt;nom_type&gt;&#39;, car il ne s’agit pas de &#39;System.Exception&#39; ni d’une classe qui h&#233;rite de &#39;System.Exception&#39;.
`Catch` peut seulement intercepter des exceptions, et vous avez tenté d’intercepter un élément qui n’est pas dérivé d’une exception.  
  
 **ID d’erreur :** BC30392  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’instruction `Catch` ou remplacez la cible de `Catch` par une exception réelle.  
  
## Voir aussi  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Vue d’ensemble de la gestion structurée des exceptions pour Visual Basic](http://msdn.microsoft.com/fr-fr/bb81af80-a735-4873-9711-6151a48e418a)