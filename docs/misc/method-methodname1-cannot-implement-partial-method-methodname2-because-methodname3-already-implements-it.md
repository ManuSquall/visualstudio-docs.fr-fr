---
title: "La m&#233;thode &#39;&lt;nom_m&#233;thode1&gt;&#39; ne peut pas impl&#233;menter de m&#233;thode partielle &#39;&lt;nom_m&#233;thode2&gt;&#39;, car &#39;&lt;nom_m&#233;thode3&gt;&#39; l’impl&#233;mente d&#233;j&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31434"
  - "bc31434"
helpviewer_keywords: 
  - "BC31434"
ms.assetid: 61cba19e-db11-4a06-89d6-4244d411588c
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La m&#233;thode &#39;&lt;nom_m&#233;thode1&gt;&#39; ne peut pas impl&#233;menter de m&#233;thode partielle &#39;&lt;nom_m&#233;thode2&gt;&#39;, car &#39;&lt;nom_m&#233;thode3&gt;&#39; l’impl&#233;mente d&#233;j&#224;
La méthode '\<nom\_méthode1\>' ne peut pas implémenter de méthode partielle '\<nom\_méthode2\>', car '\<nom\_méthode3\>' l’implémente déjà. Une seule méthode peut implémenter une méthode partielle.  
  
 Vous ne pouvez avoir deux méthodes partielles qui implémentent la même déclaration de méthode partielle. Le code suivant génère cette erreur.  
  
```vb#  
Partial Class Product ' Declaration of the partial method. Partial Private Sub ValueChanged() End Sub End Class  
```  
  
```vb#  
Partial Class Product ' First implementation of the partial method. Private Sub ValueChanged() MsgBox(Value was changed to " & Me.Quantity) End Sub ' Second implementation of the partial method causes this error. 'Private Sub ValueChanged() '    Console.WriteLine("Quantity was changed to " & Me.Quantity) 'End Sub End Class  
```  
  
 **ID d’erreur :** BC31434  
  
## Voir aussi  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)