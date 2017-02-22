---
title: "CA1821 : Supprimer les finaliseurs vides | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RemoveEmptyFinalizers"
  - "CA1821"
helpviewer_keywords: 
  - "CA1821"
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA1821 : Supprimer les finaliseurs vides
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveEmptyFinalizers|  
|CheckId|CA1821|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type implémente un finaliseur qui est vide, appelle uniquement le finaliseur de type de base ou appelle uniquement les méthodes émises sous certaines conditions.  
  
## Description de la règle  
 Évitez autant que possible d'utiliser des finaliseurs en raison de la surcharge supplémentaire des performances impliquée dans le suivi de la durée de vie de l'objet.  Le garbage collector exécute le finaliseur avant de collecter l'objet.  Cela signifie que deux collections sont requises pour collecter l'objet.  Un finaliseur vide entraîne cette charge supplémentaire sans aucun avantage.  
  
## Comment corriger les violations  
 Supprimer le finaliseur vide.  Si un finaliseur est requis pour le débogage, insérez\-le entièrement dans les directives `#if DEBUG / #endif`.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun message de cette règle.  Ne pas parvenir à supprimer une finalisation réduit les performances et n'apporte aucun avantage.  
  
## Exemple  
 L'exemple suivant indique un finaliseur vide qui doit être supprimé, un finaliseur qui doit être inséré dans les directives `#if DEBUG / #endif` et un finaliseur qui utilise les directives `#if DEBUG / #endif` correctement.  
  
 [!code-cs[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]