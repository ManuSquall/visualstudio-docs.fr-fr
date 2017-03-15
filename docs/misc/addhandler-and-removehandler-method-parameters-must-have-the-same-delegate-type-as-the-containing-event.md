---
title: "Les param&#232;tres de m&#233;thode &#39;AddHandler&#39; et &#39;RemoveHandler&#39; doivent avoir le m&#234;me type d&#233;l&#233;gu&#233; que l’&#233;v&#233;nement conteneur | Microsoft Docs"
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
  - "bc31136"
  - "vbc31136"
helpviewer_keywords: 
  - "BC31136"
ms.assetid: 199b2f7b-a85e-465d-9853-0995156e7ab6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les param&#232;tres de m&#233;thode &#39;AddHandler&#39; et &#39;RemoveHandler&#39; doivent avoir le m&#234;me type d&#233;l&#233;gu&#233; que l’&#233;v&#233;nement conteneur
Une déclaration `Custom Event` doit comporter des déclarations `AddHandler` ou `RemoveHandler`, chacune d’elles prenant un paramètre unique du type délégué spécifié par la clause `As` de l’événement personnalisé.  
  
 **ID d’erreur :** BC31136  
  
### Pour corriger cette erreur  
  
-   Remplacez le type du paramètre par le type délégué spécifié par la clause `As` de l’événement personnalisé.  
  
## Exemple  
 Cet exemple montre un événement personnalisé avec les types de paramètres appropriés pour les déclarations `AddHandler` et `RemoveHandler`.  
  
 [!code-vb[VbVbalrEventError#1](../misc/codesnippet/VisualBasic/addhandler-and-removehandler-method-parameters-must-have-the-same-delegate-type-as-the-containing-event_1.vb)]  
  
## Voir aussi  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- delete](http://msdn.microsoft.com/fr-fr/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/fr-fr/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)