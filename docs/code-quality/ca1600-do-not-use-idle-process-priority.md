---
title: 'CA1600 : Ne pas utiliser de priorité de processus inactif | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: 93255488efa84f553d61aaedb0474c69a4bbb8d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600 : Ne pas utiliser de priorité de processus inactif
|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|Category|Microsoft.Mobility|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Cette règle se produit lorsque le processus ont la valeur `ProcessPriorityClass.Idle`.  
  
## <a name="rule-description"></a>Description de la règle  
 N'affectez pas la valeur Idle à la priorité de processus. Processus qui ont `System.Diagnostics.ProcessPriorityClass.Idle` occuperaient le processeur lorsqu’il devrait être inactif et bloque par conséquent la veille.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 La valeur processus `ProcessPriorityClass.BelowNormal`.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Cette règle doit être supprimée uniquement lorsque la priorité de processus inactif est requise et considérations relatives à la mobilité peut être ignoré en toute sécurité.