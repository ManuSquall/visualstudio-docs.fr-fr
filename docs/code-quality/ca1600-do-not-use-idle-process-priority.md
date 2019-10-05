---
title: 'CA1600 : Ne pas utiliser de priorité de processus inactif'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 686929471ee8b6b5d1896f61bcbcd97a59135462
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234379"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600 : Ne pas utiliser de priorité de processus inactif

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Category|Microsoft.Mobility|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Cette règle se produit lorsque les processus ont `ProcessPriorityClass.Idle`la valeur.

## <a name="rule-description"></a>Description de la règle
N'affectez pas la valeur Idle à la priorité de processus. Les processus qui `System.Diagnostics.ProcessPriorityClass.Idle` ont l’occuperont le processeur lorsque celui-ci serait inactif et bloquera donc la mise en veille.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Affectez à `ProcessPriorityClass.BelowNormal`processus la valeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Cette règle doit être supprimée uniquement lorsque la priorité du processus inactif est requise et que les considérations relatives à la mobilité peuvent être ignorées en toute sécurité.