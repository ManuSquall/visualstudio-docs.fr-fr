---
title: "Les arguments de type ne peuvent pas &#234;tre appliqu&#233;s &#224; l’expression &#39;&lt;expression&gt;&#39; | Microsoft Docs"
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
  - "bc32058"
  - "vbc32058"
helpviewer_keywords: 
  - "BC32058"
ms.assetid: c6b9b49c-6fb2-47b8-a8bb-464562d3adfd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les arguments de type ne peuvent pas &#234;tre appliqu&#233;s &#224; l’expression &#39;&lt;expression&gt;&#39;
Un alias d’importation est défini avec une clause [Of](/dotnet/visual-basic/language-reference/statements/of-clause) qui passe des arguments de type à l’alias d’importation.  
  
 Les arguments de type sont utilisés pour les types génériques, et seuls les classes, structures, interfaces, procédures et délégués peuvent être génériques. Ni les espaces de noms, ni les alias d’importation ne peuvent être génériques.  
  
 **ID d’erreur :** BC32058  
  
### Pour corriger cette erreur  
  
-   Supprimez la clause `Of` et ses arguments de type de l’alias d’importation.  
  
## Voir aussi  
 [Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [References and the Imports Statement](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)   
 [NOT IN BUILD : Résolution d’une référence quand plusieurs variables portent le même nom](http://msdn.microsoft.com/fr-fr/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)