---
title: "D&#233;pannage des exceptions&#160;: System.DivideByZeroException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DivideByZeroException (classe)"
ms.assetid: ddc79201-3ba1-455f-8496-edaad792ccf1
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.DivideByZeroException
Une exception <xref:System.DivideByZeroException> est levée lors d'une tentative de division par zéro d'une valeur entière ou décimale.  
  
## Conseils associés  
 **Assurez\-vous que la valeur du dénominateur est différente de zéro avant d'effectuer une division.**  
 La division d'une valeur à virgule flottante par zéro a pour résultat l'infini positif, l'infini négatif ou une valeur non numérique \(NaN\), selon les règles arithmétiques de la norme IEEE. Les opérations à virgule flottante ne lèvent jamais d'exception.  
  
## Voir aussi  
 <xref:System.DivideByZeroException>   
 [Arithmetic Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators)   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)