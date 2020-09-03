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
ms.openlocfilehash: 3f6233136dcf7f1db5d622a02419d33e0eedacf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545676"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600 : Ne pas utiliser de priorité de processus inactif
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Category|Microsoft. Mobility|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 Cette règle se produit lorsque les processus ont la valeur `ProcessPriorityClass.Idle` .

## <a name="rule-description"></a>Description de la règle
 N'affectez pas la valeur Idle à la priorité de processus. Les processus qui ont `System.Diagnostics.ProcessPriorityClass.Idle` l’occuperont le processeur lorsque celui-ci serait inactif et bloquera donc la mise en veille.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Affectez à processus la valeur `ProcessPriorityClass.BelowNormal` .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Cette règle doit être supprimée uniquement lorsque la priorité du processus inactif est requise et que les considérations relatives à la mobilité peuvent être ignorées en toute sécurité.
