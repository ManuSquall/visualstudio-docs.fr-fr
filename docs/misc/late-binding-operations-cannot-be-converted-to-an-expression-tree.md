---
title: "Impossible de convertir les op&#233;rations &#224; liaison tardive en une arborescence de l’expression | Microsoft Docs"
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
  - "vbc36604"
  - "bc36604"
helpviewer_keywords: 
  - "BC36604"
ms.assetid: 6fd66d12-8c99-46e0-9095-fe1b29fd2692
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de convertir les op&#233;rations &#224; liaison tardive en une arborescence de l’expression
Une tentative de conversion d’une opération de liaison tardive a été effectuée dans une arborescence de l’expression. Ce n’est pas valide. Par exemple, le code suivant génère cette erreur.  
  
```vb#  
Option Strict Off Module Module1 Sub Main() '' Not valid. ' Test(Function(someInstance) someInstance.SomeProperty) End Sub Sub Test(ByVal ex As Expressions.Expression(Of Func(Of Object, Object))) End Sub End Module  
```  
  
 **ID d’erreur :** BC36604  
  
## Voir aussi  
 [Early and Late Binding](/dotnet/visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding)   
 [NOT IN BUILD : Arborescences de l’expression dans LINQ](http://msdn.microsoft.com/fr-fr/1a2e8e74-4bbc-45ab-9a46-2b6cfce3bcb2)