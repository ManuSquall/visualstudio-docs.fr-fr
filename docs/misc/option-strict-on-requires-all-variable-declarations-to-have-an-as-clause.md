---
title: "Toutes les d&#233;clarations de variable d’Option&#160;Strict&#160;On exigent une clause&#160;&#39;As&#39; | Microsoft Docs"
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
  - "bc30209"
  - "vbc30209"
helpviewer_keywords: 
  - "BC30209"
ms.assetid: 69c2e32a-86aa-4075-a142-440605a7063a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Toutes les d&#233;clarations de variable d’Option&#160;Strict&#160;On exigent une clause&#160;&#39;As&#39;
Une déclaration contient une variable déclarée sans clause `As`. Quand `Option Strict` a la valeur `On`, chaque variable, propriété, argument de procédure et retour de fonction doit être déclaré avec une clause `As` pour spécifier son type de données ; par exemple, `Dim MyNum As Short`.  
  
 **ID d’erreur :** BC30209  
  
### Pour corriger cette erreur  
  
1.  Vérifiez si le mot clé `As` est mal orthographié.  
  
2.  Fournissez une clause `As` pour la variable déclarée, ou activez `Option Strict Off`.  
  
## Voir aussi  
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Déclaration de variable](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)