---
title: "Le param&#232;tre &#39;ByRef&#39; &lt;nom_param&#232;tre&gt; ne peut pas &#234;tre utilis&#233; dans une expression de requ&#234;te. | Microsoft Docs"
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
  - "vbc36533"
  - "bc36533"
helpviewer_keywords: 
  - "BC36533"
ms.assetid: 8067ac87-dd6b-4869-87d0-8a4ce272de41
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre &#39;ByRef&#39; &lt;nom_param&#232;tre&gt; ne peut pas &#234;tre utilis&#233; dans une expression de requ&#234;te.
Une requête LINQ contient un paramètre qui est un type pointeur. Les paramètres utilisés dans les expressions de requête ne peuvent pas être passés par référence.  
  
 **ID d’erreur :** BC36533  
  
### Pour corriger cette erreur  
  
1.  Déclarez une nouvelle variable, puis assignez la valeur de cette nouvelle variable à une copie de la valeur passée par référence. Utilisez la variable copiée dans la requête LINQ. Voici un exemple :  
  
    ```vb#  
    Sub RunQuery(ByVal collection As List(Of Integer), _  
                 ByRef filterValue As Integer)  
        Dim fv = filterValue  
        Dim queryResult = From num In collection _  
                          Where num < fv  
    End Sub  
    ```  
  
### Pour corriger cette erreur  
  
1.  Remplacez le mot clé `ByRef` par le mot clé `ByVal` pour le paramètre utilisé dans la requête.  
  
## Voir aussi  
 [Differences Between Passing an Argument By Value and By Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)