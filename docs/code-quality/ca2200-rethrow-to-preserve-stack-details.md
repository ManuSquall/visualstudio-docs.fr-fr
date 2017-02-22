---
title: "CA2200&#160;: Levez &#224; nouveau une exception pour conserver les d&#233;tails de la pile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RethrowToPreserveStackDetails"
  - "CA2200"
helpviewer_keywords: 
  - "CA2200"
  - "RethrowToPreserveStackDetails"
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2200&#160;: Levez &#224; nouveau une exception pour conserver les d&#233;tails de la pile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RethrowToPreserveStackDetails|  
|CheckId|CA2200|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une exception est à nouveau levée et est spécifiée explicitement dans l'instruction `throw`.  
  
## Description de la règle  
 Une fois qu'une exception est levée, une partie des informations qu'elle véhicule constitue la trace de la pile.  La trace de la pile consiste en une liste de la hiérarchie d'appels de méthode, qui démarre avec la méthode qui lève l'exception et s'achève avec la méthode qui intercepte l'exception.  Si une exception est à nouveau levée par sa spécification dans l'instruction `throw`, la trace de la pile est redémarrée au niveau de la méthode actuelle et la liste des appels de méthode présents entre la méthode d'origine qui a levé l'exception et la méthode actuelle est perdue.  Pour conserver les informations de traçage de la pile d'origine avec l'exception, utilisez l'instruction `throw` sans spécifier l'exception.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, levez à nouveau l'exception sans la spécifier explicitement.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente une méthode, `CatchAndRethrowExplicitly`, qui viole la règle et une méthode, `CatchAndRethrowImplicitly`, qui satisfait à la règle.  
  
 [!CODE [FxCop.Usage.Rethrow#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow#1)]