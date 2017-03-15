---
title: "Le param&#232;tre &#39;&lt;nom_param&#232;tre&gt;&#39; dans &#39;&lt;nom_m&#233;thode&gt;&#39; a d&#233;j&#224; un argument omis correspondant | Microsoft Docs"
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
  - "vbc32021"
  - "bc32021"
helpviewer_keywords: 
  - "BC32021"
ms.assetid: f51d29ba-c5b3-4731-a426-4c5ba11b4e1f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre &#39;&lt;nom_param&#232;tre&gt;&#39; dans &#39;&lt;nom_m&#233;thode&gt;&#39; a d&#233;j&#224; un argument omis correspondant
Un appel de procédure fournit un argument par nom après omission du même argument par position. Par exemple :  
  
```  
Public Sub ABC(ByVal X As Byte, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) ' ... Call ABC(6, , Y:=3)   ' Argument Y omitted by position, supplied by name.  
```  
  
 **ID d’erreur :** BC32021  
  
### Pour corriger cette erreur  
  
-   Fournissez l’argument par position ou supprimez la virgule qui provoque son omission.  
  
## Voir aussi  
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)