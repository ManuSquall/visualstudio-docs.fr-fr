---
title: "CA1601 : Ne pas utiliser de minuteries qui empêchent les changements d’état d’alimentation | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4fb8ef82581f60cea3eb121e3d0c68fbffa82d8a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601 : Ne pas utiliser de minuteries qui empêchent les changements d'état de l'alimentation
|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|Category|Microsoft.Mobility|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Une minuterie a un intervalle défini pour se produire plusieurs fois par seconde.  
  
## <a name="rule-description"></a>Description de la règle  
 Des interrogations plus souvent qu’une seule fois par seconde ou utiliser des minuteries qui se produisent plus fréquemment qu’une fois par seconde. En effet, toute activité périodique supérieure à cette fréquence occupe le processeur et interfère avec les minuteries d'inactivité qui déclenchent la mise en veille de l'écran et des disques durs pour économiser de l'énergie.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Définir les intervalles de minuteur se produire moins d’une fois par seconde.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Cette règle doit être supprimée uniquement si le déclenchement de la minuterie plus d’une fois par seconde est requis et considérations relatives à la mobilité peut être ignoré sans risque.