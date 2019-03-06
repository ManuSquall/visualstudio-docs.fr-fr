---
title: avertissements liés à la mobilité
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 170caf52999fb687c040c2e9212d1a1ed2e154a0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55908412"
---
# <a name="mobility-warnings"></a>avertissements liés à la mobilité
Avertissements de mobilité prennent en charge la consommation d’énergie efficace.

## <a name="in-this-section"></a>Dans cette section

|Règle|Description|
|----------|-----------------|
|[CA1600 : N’utilisez pas de priorité de processus inactif](../code-quality/ca1600-do-not-use-idle-process-priority.md)|N'affectez pas la valeur Idle à la priorité de processus. Sinon, les processus avec System.Diagnostics.ProcessPriorityClass.Idle occuperaient le processeur alors qu'il devrait être inactif et bloqueraient par conséquent la veille.|
|[CA1601 : Ne pas utiliser de minuteries qui empêchent les changements d’état d’alimentation](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|En effet, toute activité périodique supérieure à cette fréquence occupe le processeur et interfère avec les minuteries d'inactivité qui déclenchent la mise en veille de l'écran et des disques durs pour économiser de l'énergie.|