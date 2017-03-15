---
title: "Le nom de param&#232;tre &#39;&lt;nom_param&#232;tre1&gt;&#39; ne correspond pas au nom du param&#232;tre correspondant, &#39;&lt;nom_param&#232;tre2&gt;&#39;, d&#233;fini dans la d&#233;claration de m&#233;thode partielle &#39;&lt;nom_m&#233;thode&gt;&#39; | Microsoft Docs"
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
  - "vbc31442"
  - "bc31442"
helpviewer_keywords: 
  - "BC31442"
ms.assetid: 7f097bb2-071a-42ec-b7af-40da04f602f2
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le nom de param&#232;tre &#39;&lt;nom_param&#232;tre1&gt;&#39; ne correspond pas au nom du param&#232;tre correspondant, &#39;&lt;nom_param&#232;tre2&gt;&#39;, d&#233;fini dans la d&#233;claration de m&#233;thode partielle &#39;&lt;nom_m&#233;thode&gt;&#39;
Quand les paramètres sont fournis pour la déclaration et l’implémentation d’une méthode partielle, les noms des paramètres correspondants doivent être les mêmes. Par exemple, le code suivant génère cette erreur.  
  
```vb#  
Partial Class Product  
  
    ' Declaration of the partial method.  
    Partial Private Sub valueChanged(ByVal newVal As Integer)  
    End Sub  
End Class  
```  
  
```vb#  
Partial Class Product  
  
    ' Implementation of the partial method. This error is  
    ' reported for parameter val.  
    ' Private Sub valueChanged(ByVal val As Integer)  
    '     MsgBox(Value was changed to " & Me.Quantity)  
    ' End Sub  
  
End Class  
```  
  
 **ID d’erreur :** BC31442  
  
### Pour corriger cette erreur  
  
1.  Modifiez le nom des paramètres de la déclaration ou de l’implémentation pour que les paramètres correspondants portent le même nom.  
  
## Voir aussi  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)