---
title: "Les op&#233;randes &#39;If&#39; ne peuvent pas &#234;tre des arguments nomm&#233;s | Microsoft Docs"
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
  - "bc33105"
  - "vbc33105"
helpviewer_keywords: 
  - "BC33105"
ms.assetid: 596baeb6-a44f-4d92-beb7-06624b60c00d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les op&#233;randes &#39;If&#39; ne peuvent pas &#234;tre des arguments nomm&#233;s
L’utilisation d’arguments nommés dans les opérandes de l’opérateur `If` n’est pas valide. L’exemple suivant génère cette erreur :  
  
```  
Dim i As Integer Dim result As String ' Not valid. ' result = (If(i > 0, TruePart:="positive", FalsePart:="not positive")  
```  
  
 Il diffère de la fonction `IIf` qui autorise des arguments nommés, comme indiqué dans le code suivant :  
  
```  
' Valid. IIf(i > 0, TruePart:="positive", FalsePart:="not positive")  
```  
  
 **ID d’erreur :** BC33105  
  
### Pour corriger cette erreur  
  
-   Supprimez les assignations de nom des opérandes, comme indiqué dans le code suivant.  
  
    ```  
    result = If(i > 0, "positive", "not positive")  
    ```  
  
## Voir aussi  
 [If Operator](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)