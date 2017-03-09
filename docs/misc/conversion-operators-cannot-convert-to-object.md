---
title: "Les op&#233;rateurs de conversion ne peuvent pas se convertir en Object | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33028"
  - "vbc33028"
helpviewer_keywords: 
  - "BC33028"
ms.assetid: 064b478c-85a1-4e13-a292-d8aebb079cad
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les op&#233;rateurs de conversion ne peuvent pas se convertir en Object
Un opérateur de conversion est déclaré avec un type de retour de [Object Data Type](/dotnet/visual-basic/language-reference/data-types/object-data-type).  
  
 Au moment de la compilation, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] considère qu’une conversion prédéfinie existe de tout type référence en tout type dans sa hiérarchie d’héritage, c’est\-à\-dire tout type duquel il dérive ou qui en dérive.`Object` est le type de données universel dans [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], si bien que chaque type dérive de `Object`.  
  
 Étant donné que le compilateur considère cette conversion comme étant déjà définie, il ne vous permet pas de la redéfinir.  
  
 **ID d’erreur :** BC33028  
  
### Pour corriger cette erreur  
  
-   Supprimez entièrement la définition de cet opérateur. Il est déjà prédéfini.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Objet en tant que type de données universel \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/5315bf21-2b22-45ab-98cd-5631dffbcb2f)