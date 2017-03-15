---
title: "CA1802&#160;: Utilisez des litt&#233;raux lorsque n&#233;cessaire | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
helpviewer_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1802&#160;: Utilisez des litt&#233;raux lorsque n&#233;cessaire
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un champ est déclaré `static` et `readonly` \(`Shared` et `ReadOnly` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), et est initialisé avec une valeur qui est calculable à la compilation.  
  
## Description de la règle  
 La valeur d'un champ `static` `readonly` est calculée à l'exécution lorsque le constructeur statique du type déclarant est appelé.  Si le champ `static` `readonly` est initialisé lorsqu'il est déclaré et qu'un constructeur statique n'est pas déclaré explicitement, le compilateur émet un constructeur statique pour initialiser le champ.  
  
 La valeur d'un champ `const` est calculée à la compilation et stockée dans les métadonnées, ce qui améliore les performances d'exécution lorsqu'il est comparé à un champ `static` `readonly`.  
  
 La valeur assignée au champ ciblé étant calculable à la compilation, remplacez la déclaration par un champ `const` afin que la valeur soit calculée à la compilation plutôt qu'à l'exécution.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, remplacez les modificateurs `static` et `readonly` par le modificateur `const`.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle, voire de désactiver la règle, si les performances ne sont pas un problème.  
  
## Exemple  
 L'exemple suivant présente un type, `UseReadOnly`, qui enfreint la règle et un autre, `UseConstant`, qui satisfait la règle.  
  
 [!CODE [FxCop.Performance.UseLiterals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals#1)]