---
title: "Les param&#232;tres de m&#233;thode &#39;AddHandler&#39; et &#39;RemoveHandler&#39; ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;ByRef&#39; | Microsoft Docs"
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
  - "vbc31134"
  - "bc31134"
helpviewer_keywords: 
  - "BC31134"
ms.assetid: 942f0b91-e71a-499a-ad10-a5dfcb4e72b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les param&#232;tres de m&#233;thode &#39;AddHandler&#39; et &#39;RemoveHandler&#39; ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;ByRef&#39;
Les paramètres des méthodes `AddHandler` et `RemoveHandler` ne peuvent pas être déclarés avec le modificateur `ByRef`.  
  
 **ID d’erreur :** BC31134  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `ByRef` du paramètre.  
  
## Voir aussi  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- delete](http://msdn.microsoft.com/fr-fr/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/fr-fr/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)