---
title: "Le param&#232;tre &#39;&lt;nom_param&#232;tre&gt;&#39; a d&#233;j&#224; un argument omis correspondant | Microsoft Docs"
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
  - "vbc36566"
  - "bc36566"
helpviewer_keywords: 
  - "BC36566"
ms.assetid: b37af6bc-abd0-4436-bf8a-a467e3603342
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre &#39;&lt;nom_param&#232;tre&gt;&#39; a d&#233;j&#224; un argument omis correspondant
Un appel de procédure fournit un argument par nom après omission du même argument par position. Voici un exemple :  
  
```vb#  
Public Sub ABC(ByVal X As Byte, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) ' ... ' Argument Y is omitted by position, but supplied by name. Call ABC(6, , Y:=3)     
```  
  
 **ID d’erreur :** BC36566  
  
### Pour corriger cette erreur  
  
-   Fournissez l’argument par position ou supprimez la virgule qui provoque son omission.  
  
## Voir aussi  
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)