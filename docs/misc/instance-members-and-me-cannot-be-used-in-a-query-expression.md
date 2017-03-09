---
title: "Les membres d’instance et &#39;Me&#39; ne peuvent pas &#234;tre utilis&#233;s dans une expression de requ&#234;te | Microsoft Docs"
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
  - "vbc36535"
  - "bc36535"
helpviewer_keywords: 
  - "BC36535"
ms.assetid: afb5281b-70a7-48c7-a46d-39522b96b1ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les membres d’instance et &#39;Me&#39; ne peuvent pas &#234;tre utilis&#233;s dans une expression de requ&#234;te
Une requête LINQ dans une contrainte `Structure` inclut une référence à `Me` ou à un membre d’instance de la structure. Les références à `Me` ou les membres d’instance ne sont pas autorisés dans les expressions de requête au sein d’une contrainte `Structure`.  
  
 **ID d’erreur :** BC36535  
  
### Pour corriger cette erreur  
  
1.  Créez une copie d’un membre d’instance ou la valeur retournée par la référence à `Me` et utilisez la copie dans l’expression de requête, comme l’illustre l’exemple suivant.  
  
    ```vb#  
    Structure SampleStructure Public SearchValue As Integer Public Sub SetSearchValue(ByVal number As Integer) SearchValue = number End Sub Public Sub GetData() Dim sv = SearchValue Dim SampleData = New Integer() {1, 2, 3, 4} Dim query = From number In SampleData _ Where number < sv End Sub End Structure  
    ```  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)   
 [Me](http://msdn.microsoft.com/fr-fr/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [Structure \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)