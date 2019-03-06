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
ms.openlocfilehash: a1774b3feb2da4939420bf75506892aac6dedd72
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955789"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600 : Ne pas utiliser de priorité de processus inactif

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Category|Microsoft.Mobility|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Cette règle se déclenche lorsque les processus sont définies sur `ProcessPriorityClass.Idle`.

## <a name="rule-description"></a>Description de la règle
 N'affectez pas la valeur Idle à la priorité de processus. Processus ayant `System.Diagnostics.ProcessPriorityClass.Idle` occupent le processeur alors qu’il devrait être inactif et bloque par conséquent la veille.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Définir des processus `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Cette règle doit être supprimée uniquement lorsque la priorité de processus inactif est requise et considérations sur la mobilité peuvent être ignorées en toute sécurité.