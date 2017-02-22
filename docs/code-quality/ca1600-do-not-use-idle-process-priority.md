---
title: "CA1600&#160;: Ne pas utiliser de priorit&#233; de processus inactif | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotUseIdleProcessPriority"
  - "CA1600"
helpviewer_keywords: 
  - "CA1600"
  - "DoNotUseIdleProcessPriority"
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1600&#160;: Ne pas utiliser de priorit&#233; de processus inactif
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|Catégorie|Microsoft.Mobility|  
|Modification avec rupture|Oui|  
  
## Cause  
 Cette règle se produit lorsque les processus ont la valeur `ProcessPriorityClass.Idle`.  
  
## Description de la règle  
 Ne définissez pas de priorité de processus inactif.  Les processus qui ont `System.Diagnostics.ProcessPriorityClass.Idle` occuperaient le processeur alors qu'il devrait être inactif et bloqueraient par conséquent la veille.  
  
## Comment corriger les violations  
 Affectez `ProcessPriorityClass.BelowNormal` aux processus.  
  
## Quand supprimer les avertissements  
 Cette règle doit être supprimée uniquement lorsque la priorité de processus Idle est requise et que les considérations sur la mobilité peuvent être ignorées sans risque.