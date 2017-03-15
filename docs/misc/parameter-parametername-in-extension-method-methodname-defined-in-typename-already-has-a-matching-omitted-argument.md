---
title: "Le param&#232;tre &#39;&lt;nom_param&#232;tre&gt;&#39; dans une m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;fini dans &#39;&lt;nom_type&gt;&#39; a un argument omis correspondant | Microsoft Docs"
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
  - "bc36583"
  - "vbc36583"
helpviewer_keywords: 
  - "BC36583"
ms.assetid: 662072fa-abb8-43c3-8ca2-aefb20f2e902
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre &#39;&lt;nom_param&#232;tre&gt;&#39; dans une m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;fini dans &#39;&lt;nom_type&gt;&#39; a un argument omis correspondant
Un appel de procédure à une méthode d’extension omet un argument par position, puis fournit l’argument par nom. Par exemple, l’appel suivant à la méthode d’extension `ABC` omet tout d’abord un argument pour le paramètre `Y`, puis le fournit par nom.  
  
```  
<Extension()> _ Public Sub ABC(ByVal X As Integer, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) End Sub ' . . . ' Calling extension method ABC. Dim number As Integer ' Not valid. ' number.ABC(, 4, Y:=5)  
```  
  
 **ID d’erreur :** BC36583  
  
### Pour corriger cette erreur  
  
-   Fournissez l’argument par position ou supprimez la virgule qui provoque son omission.  
  
## Voir aussi  
 [méthodes d'extension.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)