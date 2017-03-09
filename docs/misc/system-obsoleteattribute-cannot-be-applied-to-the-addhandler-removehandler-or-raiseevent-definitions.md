---
title: "&#39;System.ObsoleteAttribute&#39; ne peut pas &#234;tre appliqu&#233; aux d&#233;finitions &#39;AddHandler&#39;, &#39;RemoveHandler&#39; ou &#39;RaiseEvent&#39; | Microsoft Docs"
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
  - "bc31142"
  - "vbc31142"
helpviewer_keywords: 
  - "BC31142"
ms.assetid: 2bddde2e-9ca0-4f72-8910-0789a6350af8
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.ObsoleteAttribute&#39; ne peut pas &#234;tre appliqu&#233; aux d&#233;finitions &#39;AddHandler&#39;, &#39;RemoveHandler&#39; ou &#39;RaiseEvent&#39;
'System.ObsoleteAttribute' ne peut pas être appliqué aux définitions 'AddHandler', 'RemoveHandler' ou 'RaiseEvent'. Si nécessaire, appliquez l’attribut directement à l’événement.  
  
 Un événement personnalisé applique <xref:System.ObsoleteAttribute> à sa procédure `AddHandler`, `RemoveHandler` ou `RaiseEvent`.  
  
 <xref:System.ObsoleteAttribute> marque un élément de programmation comme n’étant plus utilisé et informe les utilisateurs que l’élément doit être supprimé des versions ultérieures du produit.  
  
 Il n’y a pas lieu d’avoir certaines parties d’un événement personnalisé en cours d’utilisation et d’autres qui ne le sont plus.  
  
 **ID d’erreur :** BC31142  
  
### Pour corriger cette erreur  
  
-   Supprimez <xref:System.ObsoleteAttribute> de la déclaration de procédure individuelle et appliquez\-le à la déclaration d’événement globale.  
  
## Voir aussi  
 <xref:System.ObsoleteAttribute>   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler Statement](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [RemoveHandler Statement](/dotnet/visual-basic/language-reference/statements/removehandler-statement)   
 [RaiseEvent Statement](/dotnet/visual-basic/language-reference/statements/raiseevent-statement)