---
title: "CA1601&#160;: Ne pas utiliser de minuteries qui emp&#234;chent les changements d&#39;&#233;tat de l&#39;alimentation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
helpviewer_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1601&#160;: Ne pas utiliser de minuteries qui emp&#234;chent les changements d&#39;&#233;tat de l&#39;alimentation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|Catégorie|Microsoft.Mobility|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une minuterie a un intervalle défini pour se déclencher plus d'une fois par seconde.  
  
## Description de la règle  
 Évitez d'effectuer des interrogations ou d'utiliser des minuteries qui se déclenchent plus d'une fois par seconde.  En effet, toute activité périodique supérieure à cette fréquence occupe le processeur et interfère avec les minuteries d'inactivité qui déclenchent la mise en veille de l'écran et des disques durs pour économiser de l'énergie.  
  
## Comment corriger les violations  
 Définissez des intervalles pour la minuterie pour qu'elle se déclenche moins d'une fois par seconde.  
  
## Quand supprimer les avertissements  
 Cette règle doit être supprimée uniquement si le déclenchement de la minuterie plus d'une fois par seconde est requis et si les considérations sur la mobilité peuvent être ignorées sans risque.