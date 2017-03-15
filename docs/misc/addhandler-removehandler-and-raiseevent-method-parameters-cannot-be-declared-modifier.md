---
title: "Les param&#232;tres de m&#233;thode &#39;AddHandler&#39;, &#39;RemoveHandler&#39; et &#39;RaiseEvent&#39; ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;&lt;modificateur&gt;&#39; | Microsoft Docs"
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
  - "vbc31138"
  - "bc31138"
helpviewer_keywords: 
  - "BC31138"
ms.assetid: 6d8df92a-95fc-4a7d-ab1e-06d312155c55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les param&#232;tres de m&#233;thode &#39;AddHandler&#39;, &#39;RemoveHandler&#39; et &#39;RaiseEvent&#39; ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;&lt;modificateur&gt;&#39;
Les paramètres des méthodes `AddHandler`, `RemoveHandler` et `RaiseEvent` ne peuvent pas être déclarés avec les modificateurs `Optional` ou `ParamArray`.  
  
 Les modificateurs `Optional` ou `ParamArray` sont autorisés uniquement sur les paramètres dans les déclarations `Declare`, `Function`, `Property` et `Sub`.  
  
 **ID d’erreur :** BC31138  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Optional` ou `ParamArray` de la liste de paramètres.  
  
## Voir aussi  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- delete](http://msdn.microsoft.com/fr-fr/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/fr-fr/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- delete](http://msdn.microsoft.com/fr-fr/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)