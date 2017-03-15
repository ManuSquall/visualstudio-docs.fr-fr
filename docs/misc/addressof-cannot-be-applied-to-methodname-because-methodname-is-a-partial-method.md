---
title: "&#39;AddressOf&#39; ne peut pas &#234;tre appliqu&#233; &#224; &#39;methodname&#39;, car &#39;methodname&#39; est une m&#233;thode partielle | Microsoft Docs"
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
  - "vbc31440"
  - "bc31440"
helpviewer_keywords: 
  - "BC31440"
ms.assetid: 924dbada-3e0a-4004-a3ae-a209b7c3d1fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddressOf&#39; ne peut pas &#234;tre appliqu&#233; &#224; &#39;methodname&#39;, car &#39;methodname&#39; est une m&#233;thode partielle
Une méthode partielle a été passée à l’opérateur `AddressOf`. Les méthodes partielles sont des valeurs non valides pour l’opérateur `AddressOf`.  
  
 **ID d’erreur :** BC31440  
  
### Pour corriger cette erreur  
  
1.  Ajoutez une méthode d’implémentation pour la méthode partielle. La méthode d’implémentation est une valeur valide pour l’opérateur `AddressOf`. L’exemple suivant illustre une signature de méthode partielle et son implémentation.  
  
    ```vb#  
    ' Definition of the partial method signature.  
    Partial Private Sub OnNameChanged()  
        ' The body of the signature is empty.  
    End Sub  
  
    ' Implementation of the partial method.  
    Private Sub OnNameChanged()  
        MsgBox("Name was changed to " & Me.Name)  
    End Sub  
    ```  
  
## Voir aussi  
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)