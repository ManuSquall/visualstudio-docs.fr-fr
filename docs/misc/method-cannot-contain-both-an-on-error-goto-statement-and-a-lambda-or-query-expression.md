---
title: "Une m&#233;thode ne peut pas contenir &#224; la fois une instruction &#39;On Error GoTo&#39; et une expression lambda ou une expression de requ&#234;te | Microsoft Docs"
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
  - "bc36595"
  - "vbc36595"
helpviewer_keywords: 
  - "BC36595"
ms.assetid: 4e7cc11e-f53d-4481-afb4-653a81d54483
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une m&#233;thode ne peut pas contenir &#224; la fois une instruction &#39;On Error GoTo&#39; et une expression lambda ou une expression de requ&#234;te
Une méthode contient à la fois une instruction `On Error Goto` et une expression lambda ou une requête LINQ. Vous ne pouvez pas ajouter à la fois une instruction `On Error Goto` et une expression lambda ou une requête LINQ dans une méthode.  
  
 **ID d’erreur :** BC36595  
  
### Pour corriger cette erreur  
  
1.  Remplacez le code de gestion des exceptions qui utilise l’instruction `On Error Goto` par une instruction `Try...Catch`.  
  
## Voir aussi  
 [Introduction à la gestion des exceptions \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/9792f16a-0cd2-40bd-ace2-f7a4344c0e52)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [On Error Statement](/dotnet/visual-basic/language-reference/statements/on-error-statement)