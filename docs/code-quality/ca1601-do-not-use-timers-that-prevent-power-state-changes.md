---
title: "CA1601 : Ne pas utiliser de minuteries qui empêchent les changements d'état de l'alimentation"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc6db6dff5ee4c4e4d387399dbf79277046d6c02
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797445"
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
 Ne demande pas plus souvent qu’une seule fois par seconde ou utiliser des minuteries qui se produisent plus fréquemment qu’une fois par seconde. En effet, toute activité périodique supérieure à cette fréquence occupe le processeur et interfère avec les minuteries d'inactivité qui déclenchent la mise en veille de l'écran et des disques durs pour économiser de l'énergie.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Définissez des intervalles de minuterie se produire moins d’une fois par seconde.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Cette règle doit être supprimée uniquement si le déclenchement de la minuterie plusieurs fois par seconde est requis et considérations sur la mobilité peuvent être ignorées.