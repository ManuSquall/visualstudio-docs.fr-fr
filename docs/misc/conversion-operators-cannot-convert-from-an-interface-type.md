---
title: "Les op&#233;rateurs de conversion ne peuvent pas effectuer de conversion &#224; partir d’un type interface | Microsoft Docs"
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
  - "vbc33029"
  - "bc33029"
helpviewer_keywords: 
  - "BC33029"
ms.assetid: 0d0ee461-dd48-424b-b83a-484bfc648d4d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les op&#233;rateurs de conversion ne peuvent pas effectuer de conversion &#224; partir d’un type interface
Un opérateur de conversion est déclaré avec un type interface pour le paramètre.  
  
 Au moment de la compilation, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] considère qu’une conversion prédéfinie existe à partir d’une interface vers un type référence. Une telle conversion risque d’échouer au moment de l’exécution, mais le compilateur ne peut pas prédire les résultats de l’exécution, donc il permet la compilation d’une telle conversion.  
  
 Étant donné que le compilateur considère cette conversion comme étant déjà définie, il ne vous permet pas de la redéfinir.  
  
 **ID d’erreur :** BC33029  
  
### Pour corriger cette erreur  
  
-   Supprimez entièrement la définition de cet opérateur. Il est déjà prédéfini.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)