---
title: 'Ca1600 : ne pas utiliser la priorité de processus inactif | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d4260db808d9c50f78388cf6ba976f7ace52e6a3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669298"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600 : Ne pas utiliser de priorité de processus inactif
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Category|Microsoft. Mobility|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Cette règle se produit lorsque les processus sont définis sur `ProcessPriorityClass.Idle`.

## <a name="rule-description"></a>Description de la règle
 N'affectez pas la valeur Idle à la priorité de processus. Les processus qui ont `System.Diagnostics.ProcessPriorityClass.Idle` occuperont le processeur lorsque celui-ci serait inactif, et bloquera donc la mise en veille.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Définissez les processus sur `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Cette règle doit être supprimée uniquement lorsque la priorité du processus inactif est requise et que les considérations relatives à la mobilité peuvent être ignorées en toute sécurité.
