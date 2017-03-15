---
title: "La m&#233;thode &#39;&lt;nom_m&#233;thode1&gt;&#39; doit &#234;tre d&#233;clar&#233;e &#39;Private&#39; pour impl&#233;menter la m&#233;thode partielle &#39;&lt;nom_m&#233;thode2&gt;&#39; | Microsoft Docs"
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
  - "vbc31441"
  - "bc31441"
helpviewer_keywords: 
  - "BC31441"
ms.assetid: 4d8d19ad-0c3b-4eba-ada8-2cfa6ae795c4
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La m&#233;thode &#39;&lt;nom_m&#233;thode1&gt;&#39; doit &#234;tre d&#233;clar&#233;e &#39;Private&#39; pour impl&#233;menter la m&#233;thode partielle &#39;&lt;nom_m&#233;thode2&gt;&#39;
L’implémentation d’une méthode partielle doit être déclarée `Private`. Par exemple, le code suivant génère cette erreur.  
  
```vb#  
Partial Class Product ' Declaration of the partial method. Partial Private Sub valueChanged() End Sub End Class  
```  
  
```vb#  
Partial Class Product ' Implementation of the partial method, with Private missing, ' causes this error. 'Sub valueChanged() '    MsgBox(Value was changed to " & Me.Quantity) 'End Sub End Class  
```  
  
 **ID d’erreur :** BC31441  
  
### Pour corriger cette erreur  
  
1.  Utilisez le modificateur d’accès `Private` dans l’implémentation de la méthode partielle, comme indiqué dans l’exemple suivant.  
  
    ```vb#  
    Private Sub valueChanged() MsgBox(Value was changed to " & Me.Quantity) End Sub  
    ```  
  
## Voir aussi  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)