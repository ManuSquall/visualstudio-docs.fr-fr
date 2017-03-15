---
title: "Le param&#232;tre &#39;ByRef&#39; &#39;&lt;nom_param&#232;tre&gt;&#39; ne peut pas &#234;tre utilis&#233; dans une expression lambda | Microsoft Docs"
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
  - "bc36639"
  - "vbc36639"
helpviewer_keywords: 
  - "BC36639"
ms.assetid: 5913f9b6-2929-4c05-8dd1-00b10fcd5a83
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre &#39;ByRef&#39; &#39;&lt;nom_param&#232;tre&gt;&#39; ne peut pas &#234;tre utilis&#233; dans une expression lambda
Une expression lambda déclarée dans un élément `Sub` ou une fonction ne peut pas utiliser les paramètres `ByRef` de cet élément `Sub` ou de cette fonction. Par exemple, le code suivant provoquera cette erreur, car le paramètre `ByRef``n` est utilisé dans l’expression lambda.  
  
```  
'' Not valid.   
'Sub ExampleSub(ByRef n As Integer)  
  
'    Dim lambda = Function(p As Integer) p + n  
  
'End Sub  
```  
  
 **ID d’erreur :** BC36639  
  
### Pour corriger cette erreur  
  
-   Assignez le paramètre `ByRef` à une variable locale et utilisez la variable locale dans l’expression lambda, comme illustré dans le code suivant :  
  
    ```  
    Sub ExampleSub(ByRef n As Integer)  
  
        Dim temp = n  
        Dim lambda = Function(p As Integer) p + temp  
  
    End Sub  
    ```  
  
## Voir aussi  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)