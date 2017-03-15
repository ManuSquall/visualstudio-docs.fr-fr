---
title: "Tous les param&#232;tres de m&#233;thode de Option Strict On requi&#232;rent une clause &#39;As&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30211"
  - "bc30211"
helpviewer_keywords: 
  - "BC30211"
ms.assetid: 855795ce-8499-4525-a1de-cbb8ba364cd7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tous les param&#232;tres de m&#233;thode de Option Strict On requi&#232;rent une clause &#39;As&#39;
Une méthode contient un paramètre sans une clause `As`. Quand `Option Strict` est activé, chaque variable, propriété, argument de procédure et retour de fonction doit être déclaré avec une clause `As` pour spécifier son type de données ; par exemple, `Sub GetData(ByVal filter As String)`.  
  
 **ID d’erreur :** BC30211  
  
### Pour corriger cette erreur  
  
-   Vérifiez si le mot clé `As` est mal orthographié.  
  
-   Fournissez une clause `As` pour la variable déclarée, ou désactivez `Option Strict`.  
  
## Voir aussi  
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Sub Statement](/dotnet/visual-basic/language-reference/statements/sub-statement)   
 [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement)