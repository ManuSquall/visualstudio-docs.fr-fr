---
title: "L’argument &#39;Period&#39; doit &#234;tre inf&#233;rieur ou &#233;gal &#224; l’argument &#39;Life&#39; | Microsoft Docs"
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
  - "vbrFinancial_PeriodLELife"
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’argument &#39;Period&#39; doit &#234;tre inf&#233;rieur ou &#233;gal &#224; l’argument &#39;Life&#39;
La valeur de l’argument `Period`, qui indique la période pendant laquelle l’amortissement de la ressource est calculé, est supérieure à la valeur de l’argument `Life`.  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les arguments `Life` et `Period` sont exprimés dans la même unité. Par exemple, si `Life` est mesuré en mois, `Period` doit l’être également.  
  
## Voir aussi  
 [NOT IN BUILD : DDB, fonction](http://msdn.microsoft.com/fr-fr/c7cf8929-d158-4399-b3cb-31d897d12556)   
 [NOT IN BUILD : SYD, fonction](http://msdn.microsoft.com/fr-fr/23c25672-f5dd-49ac-9893-4faa82634181)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)