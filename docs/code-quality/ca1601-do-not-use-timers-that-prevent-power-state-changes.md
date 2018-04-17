---
title: 'CA1601 : Ne pas utiliser de minuteries qui empêchent les changements d’état d’alimentation | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 270c030d4d4b829fb1e7d17308a4ae6f0ad17539
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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