---
title: "Le modificateur &#39;Custom&#39; n’est pas valide pour les &#233;v&#233;nements d&#233;clar&#233;s dans les interfaces | Microsoft Docs"
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
  - "bc31121"
  - "vbc31121"
helpviewer_keywords: 
  - "BC31121"
ms.assetid: b5687034-a2b2-4961-88b7-0ba73023573e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le modificateur &#39;Custom&#39; n’est pas valide pour les &#233;v&#233;nements d&#233;clar&#233;s dans les interfaces
Vous ne pouvez pas déclarer un événement personnalisé dans une interface, car un événement personnalisé doit fournir une implémentation de ses méthodes `AddHandler`, `RemoverHandler` et `RaiseEvent`.  
  
 Vous pouvez utiliser le mot clé `Custom` dans une classe dérivée qui implémente l’événement.  
  
 **ID d’erreur :** BC31121  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Custom` de la déclaration d’événement dans l’interface.  
  
## Exemple  
 Cet exemple montre comment implémenter un événement déclaré dans une interface en tant qu’événement personnalisé.  
  
 [!code-vb[VbVbalrEventError#3](../misc/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-in-interfaces_1.vb)]  
  
## Voir aussi  
 [Custom \- delete](http://msdn.microsoft.com/fr-fr/dc62be07-c896-4866-a533-982a661d143f)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)