---
title: 'CA1600 : Ne pas utiliser de priorité de processus inactif | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b211c1ab646d27cf32290d3c5c306719ba7decff
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590126"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600 : Ne pas utiliser de priorité de processus inactif
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1600 : n’utilisez pas de priorité de processus inactif](https://docs.microsoft.com/visualstudio/code-quality/ca1600-do-not-use-idle-process-priority).

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



