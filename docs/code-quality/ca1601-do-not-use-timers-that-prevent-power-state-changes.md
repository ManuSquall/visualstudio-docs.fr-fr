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
ms.openlocfilehash: ed9c0e2db15c3d707823105ba4e708be466a662e
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72439956"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601 : Ne pas utiliser de minuteries qui empêchent les changements d'état de l'alimentation

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Category|Microsoft. Mobility|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
L’intervalle d’un minuteur est défini pour s’exécuter plusieurs fois par seconde.

## <a name="rule-description"></a>Description de la règle
N’interrogez pas plus d’une fois par seconde ou utilisez des minuteries qui se produisent plus souvent qu’une fois par seconde. En effet, toute activité périodique supérieure à cette fréquence occupe le processeur et interfère avec les minuteries d'inactivité qui déclenchent la mise en veille de l'écran et des disques durs pour économiser de l'énergie.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Définir des intervalles de minuterie pour qu’ils se produisent moins d’une fois par seconde.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Cette règle doit être supprimée uniquement si le déclenchement de la minuterie plus d’une fois par seconde est nécessaire et si les considérations relatives à la mobilité peuvent être ignorées en toute sécurité.
