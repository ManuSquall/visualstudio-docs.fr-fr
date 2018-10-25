---
title: 'CA1600 : Ne pas utiliser de priorité de processus inactif'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c1db098a485002d97aaf986fbac95e35519351b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924675"
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