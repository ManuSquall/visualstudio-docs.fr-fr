---
title: "D&#233;pannage des exceptions&#160;: System.OverflowException | Microsoft Docs"
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
  - "OverflowException (classe)"
ms.assetid: bd380db7-5d05-4d7f-be5b-e654fdadf14c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.OverflowException
Une exception <xref:System.OverflowException> est levée lorsqu'une opération arithmétique, de casting ou de conversion engendre un dépassement de capacité dans un contexte vérifié \(checked\). Un dépassement de capacité se produit lorsqu'une opération engendre une valeur trop grande pour le type de destination, infinie ou non numérique \(NaN\).  
  
## Conseils associés  
 **Lorsque vous effectuez un cast à partir d'un nombre, la valeur doit être un nombre valide inférieur à l'infini.**  
 Une valeur source ne peut pas être infinie ou non numérique.  
  
 **Assurez\-vous que vous ne divisez pas par zéro.**  
 La division par zéro génère habituellement cette exception.  
  
## Notes  
 Dans les langages qui détectent le dépassement de capacité, <xref:System.OverflowException> est l'exception levée en cas de dépassement. Par exemple, en C\#, le mot clé `checked` est utilisé pour détecter des conditions de dépassement de capacité. Une exception <xref:System.OverflowException> se produit uniquement dans un contexte vérifié \(checked\).  
  
 Lorsque le résultat d'une opération arithmétique de type intégral ou décimal ou d'une opération de conversion se trouve en dehors de la plage autorisée pour le type de destination :  
  
-   Dans un contexte vérifié \(checked\), une erreur de compilation se produit si l'opération est une expression constante. Sinon, une exception <xref:System.OverflowException> est levée si l'opération est effectuée au moment de l'exécution.  
  
-   Dans un contexte non vérifié \(unchecked\), le résultat est tronqué en supprimant tous les bits de poids fort qui ne tiennent pas dans le type destinataire.  
  
 Pour plus d’informations sur les plages de valeurs des types de données, consultez [Data Types](/dotnet/visual-basic/language-reference/data-types/data-type-summary), [Tableau des types intégraux](/dotnet/csharp/language-reference/keywords/integral-types-table) ou [Tableau des types virgule flottante](/dotnet/csharp/language-reference/keywords/floating-point-types-table).  
  
## Voir aussi  
 <xref:System.OverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)