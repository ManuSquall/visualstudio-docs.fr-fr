---
title: "La d&#233;finition &#39;RaiseEvent&#39; est manquante pour l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; | Microsoft Docs"
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
  - "vbc31132"
  - "bc31132"
helpviewer_keywords: 
  - "BC31132"
ms.assetid: 8f3442fd-2ed1-4dbc-83a8-f0860ec022ac
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La d&#233;finition &#39;RaiseEvent&#39; est manquante pour l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39;
Si un événement est déclaré comme `Custom`, il doit fournir une procédure pour déclencher l’événement.  
  
 **ID d’erreur :** BC31132  
  
### Pour corriger cette erreur  
  
1.  Placez une déclaration `RaiseEvent` entre l’instruction `Custom Event` et l’instruction `End Event`.  
  
2.  Vérifiez que les autres procédures de la déclaration d’événement se terminent correctement.  
  
## Voir aussi  
 [RaiseEvent Statement](/dotnet/visual-basic/language-reference/statements/raiseevent-statement)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)