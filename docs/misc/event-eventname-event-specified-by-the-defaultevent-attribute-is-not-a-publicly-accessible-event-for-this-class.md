---
title: "L’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; sp&#233;cifi&#233; par l’attribut &#39;DefaultEvent&#39; n’est pas un &#233;v&#233;nement accessible publiquement pour cette classe. | Microsoft Docs"
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
  - "vbc30770"
  - "bc30770"
helpviewer_keywords: 
  - "BC30770"
ms.assetid: 7524fba7-2a37-4bc3-b789-87d73a166575
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; sp&#233;cifi&#233; par l’attribut &#39;DefaultEvent&#39; n’est pas un &#233;v&#233;nement accessible publiquement pour cette classe.
L’attribut <xref:System.ComponentModel.DefaultEventAttribute> doit spécifier le nom d’un événement accessible publiquement dans la classe à laquelle l’attribut est appliqué.  
  
 **ID d’erreur :** BC30770  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que la classe définit un événement accessible publiquement.  
  
2.  Vérifiez que le nom de l’événement dans la classe correspond au nom spécifié par l’attribut <xref:System.ComponentModel.DefaultEventAttribute>.  
  
## Voir aussi  
 <xref:System.ComponentModel.DefaultEventAttribute>   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)