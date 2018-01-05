---
title: "CA1600 : Ne pas utiliser de priorité de processus inactif | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2d1646cd587295f2854399cfc24603ce1f1910e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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