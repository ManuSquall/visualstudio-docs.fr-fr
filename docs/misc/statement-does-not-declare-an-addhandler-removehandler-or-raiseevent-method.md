---
title: "L’instruction ne d&#233;clare pas une m&#233;thode &#39;AddHandler&#39;, &#39;RemoveHandler&#39; ou &#39;RaiseEvent&#39; | Microsoft Docs"
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
  - "vbc31113"
  - "bc31113"
helpviewer_keywords: 
  - "BC31113"
ms.assetid: f8299c9d-6030-43e5-878e-8d2b042191b5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’instruction ne d&#233;clare pas une m&#233;thode &#39;AddHandler&#39;, &#39;RemoveHandler&#39; ou &#39;RaiseEvent&#39;
L’instruction ne fournit pas d’instruction de déclaration `AddHandler`, `RemoveHandler` ou `RaiseEvent` autour d’une procédure `Custom Event`. Une déclaration d’événement personnalisée est un bloc de code placé entre les instructions `Custom Event` et `End Event`. À l’intérieur de ce bloc, chaque procédure `Custom Event` apparaît sous forme de bloc interne délimité par une instruction de déclaration et une instruction `End`.  
  
 **ID d’erreur :** BC31113  
  
### Pour corriger cette erreur  
  
-   Fournissez une instruction de déclaration `AddHandler`, `RemoveHandler` ou `RaiseEvent`.  
  
## Voir aussi  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- delete](http://msdn.microsoft.com/fr-fr/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/fr-fr/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- delete](http://msdn.microsoft.com/fr-fr/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)