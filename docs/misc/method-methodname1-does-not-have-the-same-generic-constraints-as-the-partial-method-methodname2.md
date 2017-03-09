---
title: "La m&#233;thode &#39;&lt;nom_m&#233;thode1&gt;&#39; n’a pas les m&#234;mes contraintes g&#233;n&#233;riques que la m&#233;thode partielle &#39;&lt;nom_m&#233;thode2&gt;&#39;. | Microsoft Docs"
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
  - "bc31438"
  - "vbc31438"
helpviewer_keywords: 
  - "BC31438"
ms.assetid: ea092f0c-661b-49db-80c1-76401fc8bc0b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La m&#233;thode &#39;&lt;nom_m&#233;thode1&gt;&#39; n’a pas les m&#234;mes contraintes g&#233;n&#233;riques que la m&#233;thode partielle &#39;&lt;nom_m&#233;thode2&gt;&#39;.
Vous avez défini une implémentation de méthode partielle dont les contraintes génériques diffèrent des contraintes de la déclaration de méthode partielle. Le code suivant illustre l’erreur.  
  
```vb#  
Partial Class Class1 Partial Private Sub Test(Of T As Class)(ByVal arg As T) End Sub End Class Partial Class Class1 '' The error occurs here, for Test. 'Private Sub Test(Of T As Structure)(ByVal arg As T) 'End Sub End Class  
```  
  
 **ID d’erreur :** BC31438  
  
## Voir aussi  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)