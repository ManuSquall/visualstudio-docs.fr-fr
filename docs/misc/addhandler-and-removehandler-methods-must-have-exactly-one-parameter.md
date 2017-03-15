---
title: "Les m&#233;thodes &#39;AddHandler&#39; et &#39;RemoveHandler&#39; doivent avoir exactement un param&#232;tre | Microsoft Docs"
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
  - "vbc31133"
  - "bc31133"
helpviewer_keywords: 
  - "BC31133"
ms.assetid: f6295626-dd63-408c-ab5f-76367f94d6ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les m&#233;thodes &#39;AddHandler&#39; et &#39;RemoveHandler&#39; doivent avoir exactement un param&#232;tre
Une déclaration d’événement personnalisé doit comporter des déclarations `AddHandler` ou `RemoveHandler`, chacune d’elles prenant un paramètre unique du type délégué spécifié par la clause `As` de l’événement personnalisé.  
  
 **ID d’erreur :** BC31133  
  
### Pour corriger cette erreur  
  
-   Supprimez les paramètres supplémentaires de la liste de paramètres et modifiez le type de paramètre pour qu’il soit identique au type délégué spécifié par la clause `As` de l’événement personnalisé.  
  
## Exemple  
 Cet exemple montre un événement personnalisé avec les types de paramètres appropriés pour les déclarations `AddHandler` et `RemoveHandler`.  
  
 [!code-vb[VbVbalrEventError#1](../misc/codesnippet/VisualBasic/addhandler-and-removehandler-methods-must-have-exactly-one-parameter_1.vb)]  
  
## Voir aussi  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- delete](http://msdn.microsoft.com/fr-fr/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/fr-fr/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)