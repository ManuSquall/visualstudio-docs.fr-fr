---
title: "La m&#233;thode &#39;RaiseEvent&#39; doit avoir la m&#234;me signature que le type d&#233;l&#233;gu&#233; de l’&#233;v&#233;nement conteneur &#39;&lt;signature&gt;&#39; | Microsoft Docs"
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
  - "bc31137"
  - "vbc31137"
helpviewer_keywords: 
  - "BC31137"
ms.assetid: 9db77546-9205-4fd2-baf6-6eb1b46b1f1a
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La m&#233;thode &#39;RaiseEvent&#39; doit avoir la m&#234;me signature que le type d&#233;l&#233;gu&#233; de l’&#233;v&#233;nement conteneur &#39;&lt;signature&gt;&#39;
Une déclaration `Custom Event` doit avoir une déclaration `RaiseEvent` ayant la même signature que le type délégué spécifié par la clause `As` de l’événement personnalisé.  
  
 Pour que les signatures correspondent, la déclaration `RaiseEvent` et le délégué doivent avoir le même nombre de paramètres, et les types de paramètres doivent être les mêmes.  
  
 **ID d’erreur :** BC31137  
  
### Pour corriger cette erreur  
  
-   Modifiez les paramètres de la déclaration `RaiseEvent` pour qu’ils correspondent aux paramètres du type délégué.  
  
## Exemple  
 Cet exemple montre un événement personnalisé avec les types de paramètres adaptés à la déclaration `RaiseEvent`.  
  
 [!code-vb[VbVbalrEventError#2](../misc/codesnippet/VisualBasic/raiseevent-method-must-have-the-same-signature-as-the-containing-event-s-delegate-type-signature_1.vb)]  
  
## Voir aussi  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [RaiseEvent \- supprimer](http://msdn.microsoft.com/fr-fr/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)