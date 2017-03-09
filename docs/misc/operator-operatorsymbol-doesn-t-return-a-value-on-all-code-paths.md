---
title: "L’op&#233;rateur &#39;&lt;symbole_op&#233;rateur&gt;&#39; ne retourne pas une valeur pour tous les chemins de code | Microsoft Docs"
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
  - "vbc42106"
  - "bc42106"
helpviewer_keywords: 
  - "BC42106"
ms.assetid: 175b2bc9-5233-462d-97de-9d97b003cc46
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’op&#233;rateur &#39;&lt;symbole_op&#233;rateur&gt;&#39; ne retourne pas une valeur pour tous les chemins de code
L’opérateur '\<symbole\_opérateur\>' ne retourne pas une valeur pour tous les chemins de code. Une exception de référence null peut se produire au moment de l'exécution lorsque le résultat est utilisé.  
  
 Au moins un chemin possible du code de la procédure d’opérateur ne retourne pas de valeur.  
  
 Pour retourner une valeur à partir d’une procédure d’opérateur, vous devez l’inclure dans une [Return Statement](/dotnet/visual-basic/language-reference/statements/return-statement).  
  
 Si le contrôle passe à l’instruction `End Operator`, la procédure d’opérateur retourne la valeur par défaut du type de données de la propriété. Pour plus d’informations, consultez la section relative au comportement dans [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement).  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42106  
  
### Pour corriger cette erreur  
  
-   Vérifiez votre logique de flux de contrôle et assurez\-vous que chaque chemin possible se termine par une instruction `Return`. La dernière instruction avant `End Operator` doit être une instruction `Return`.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)