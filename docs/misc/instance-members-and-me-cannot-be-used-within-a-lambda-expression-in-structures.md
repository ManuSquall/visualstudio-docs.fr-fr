---
title: "Les membres d’instance et &#39;Me&#39; ne peuvent pas &#234;tre utilis&#233;s au sein d’une expression lambda dans des structures | Microsoft Docs"
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
  - "vbc36638"
  - "bc36638"
helpviewer_keywords: 
  - "BC36638"
ms.assetid: 5c24a7c7-50f6-4ffb-9ed2-07e2abc4eaf3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les membres d’instance et &#39;Me&#39; ne peuvent pas &#234;tre utilis&#233;s au sein d’une expression lambda dans des structures
À partir d’une structure, vous avez défini une expression lambda qui fait référence à un membre d’instance de la structure ou utilise `Me`. Le code suivant illustre ces deux références non valides.  
  
```vb#  
Structure Structure1 Public InstanceMember As Integer Public Function ExampleFun() As Integer '' The error is caused by use of InstanceMember. 'Dim fun1 = Function() InstanceMember '' The error is caused by use of Me. 'Dim fun2 = Function() Me.InstanceMember 'Return fun1() End Function End Structure  
```  
  
 **ID d’erreur :** BC36638  
  
### Pour corriger cette erreur  
  
-   Assignez le membre d’instance à une variable locale et utilisez la variable locale dans votre instruction.  
  
    ```vb#  
    Public Function ExampleFunFix() As Integer Dim temp = InstanceMember Dim fun1 = Function() temp Return fun1() End Function  
    ```  
  
## Voir aussi  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Me](http://msdn.microsoft.com/fr-fr/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)