---
title: "Fonction sans clause &#39;As&#39;&#160;; type de retour Object pris par d&#233;faut | Microsoft Docs"
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
  - "BC42021"
  - "vbc42021"
helpviewer_keywords: 
  - "BC42021"
ms.assetid: c1efadf1-fba3-437b-a311-240c4d07d894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fonction sans clause &#39;As&#39;&#160;; type de retour Object pris par d&#233;faut
Une procédure `Function` ne spécifie pas de clause `As`.  
  
 Une clause `As` identifie un type de données à associer à un élément de programmation. Dans une [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement), elle spécifie le type de données de la valeur que la procédure `Function` retourne au code appelant. Si vous n’incluez pas de clause `As` dans l’instruction `Function`, le type de données de retour par défaut est `Object`.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42021  
  
### Pour corriger cette erreur  
  
-   Incluez une clause `As` dans l’instruction `Function` pour spécifier le type de données de retour.  
  
## Voir aussi  
 [Function, procédures](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)