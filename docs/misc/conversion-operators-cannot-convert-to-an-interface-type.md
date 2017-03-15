---
title: "Les op&#233;rateurs de conversion ne peuvent pas convertir en un type interface | Microsoft Docs"
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
  - "vbc33025"
  - "bc33025"
helpviewer_keywords: 
  - "BC33025"
ms.assetid: 7e13dfa3-2b70-4ca6-a8ec-159131fd2c4c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les op&#233;rateurs de conversion ne peuvent pas convertir en un type interface
Un opérateur de conversion est déclaré avec un type d’interface comme type de retour.  
  
 Au moment de la compilation, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] considère qu’une conversion prédéfinie existe dans tous les types de référence à une interface. Une telle conversion risque d’échouer au moment de l’exécution, mais le compilateur ne peut pas prédire les résultats de l’exécution, donc il permet la compilation d’une telle conversion.  
  
 Étant donné que le compilateur considère cette conversion comme étant déjà définie, il ne vous permet pas de la redéfinir.  
  
 **ID d’erreur :** BC33025  
  
### Pour corriger cette erreur  
  
-   Supprimez entièrement la définition de cet opérateur. Il est déjà prédéfini.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)