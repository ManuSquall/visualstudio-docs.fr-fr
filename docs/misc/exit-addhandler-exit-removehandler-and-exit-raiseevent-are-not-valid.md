---
title: "&#39;Exit AddHandler&#39;, &#39;Exit RemoveHandler&#39; et &#39;Exit RaiseEvent&#39; ne sont pas valides | Microsoft Docs"
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
  - "vbc31111"
  - "bc31111"
helpviewer_keywords: 
  - "BC31111"
ms.assetid: e02264f3-0645-4de5-b622-8a2a74496b64
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit AddHandler&#39;, &#39;Exit RemoveHandler&#39; et &#39;Exit RaiseEvent&#39; ne sont pas valides
'Exit AddHandler', 'Exit RemoveHandler' et 'Exit RaiseEvent' ne sont pas valides. Utilisez 'Return' pour quitter les membres d’événement.  
  
 L’instruction `Exit` ne peut pas être utilisée pour quitter les méthodes `AddHandler`, `RemoveHandler` ou `RaiseEvent` d’une déclaration `Custom Event`. Utilisez plutôt l’instruction `Return` sans spécifier d’expression de retour pour quitter la méthode.  
  
 **ID d’erreur :** BC31111  
  
### Pour corriger cette erreur  
  
-   Remplacez l’instruction `Exit` par l’instruction `Return`.  
  
     Vérifiez que l’instruction `Return` ne spécifie pas une expression de retour.  
  
## Voir aussi  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- supprimer](http://msdn.microsoft.com/fr-fr/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- supprimer](http://msdn.microsoft.com/fr-fr/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- supprimer](http://msdn.microsoft.com/fr-fr/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Return Statement](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)