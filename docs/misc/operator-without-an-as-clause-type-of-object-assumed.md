---
title: "Op&#233;rateur sans clause &#39;As&#39;&#160;; type Object pris par d&#233;faut | Microsoft Docs"
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
  - "vbc41005"
  - "bc41005"
helpviewer_keywords: 
  - "BC41005"
ms.assetid: 42be84ed-7aa6-4ac0-9dd4-663e90f13e09
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Op&#233;rateur sans clause &#39;As&#39;&#160;; type Object pris par d&#233;faut
Une procédure d’opérateur ne spécifie pas de clause `As`.  
  
 Une clause `As` identifie un type de données à associer à un élément de programmation. Dans un [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement), elle spécifie le type de données de la valeur que la procédure d’opérateur retourne au code appelant. Si vous n’incluez pas de clause `As` dans l’instruction `Operator`, le type de données de retour par défaut est `Object`.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC41005  
  
### Pour corriger cette erreur  
  
-   Incluez une clause `As` dans l’instruction `Operator` pour spécifier le type de données de retour.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)