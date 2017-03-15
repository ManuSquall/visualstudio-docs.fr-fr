---
title: "Propri&#233;t&#233; sans clause &#39;As&#39;&#160;; type Object pris par d&#233;faut | Microsoft Docs"
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
  - "BC42022"
  - "vbc42022"
helpviewer_keywords: 
  - "BC42022"
ms.assetid: 3379692b-8278-4488-878a-0afb76e554b1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propri&#233;t&#233; sans clause &#39;As&#39;&#160;; type Object pris par d&#233;faut
Une déclaration de propriété ne spécifie pas de clause `As`.  
  
 Une clause `As` identifie un type de données à associer à un élément de programmation. Dans un [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement), elle spécifie le type de données de la valeur que la procédure `Get` de la propriété retourne au code appelant. Si vous n’incluez pas de clause `As` dans l’instruction `Property`, le type de données par défaut de la propriété est `Object`.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42022  
  
### Pour corriger cette erreur  
  
-   Incluez une clause `As` dans l’instruction `Property` pour spécifier le type de données de la propriété.  
  
## Voir aussi  
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)