---
title: "Avertissements li&#233;s &#224; la mobilit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.MobilityRules"
helpviewer_keywords: 
  - "avertissements liés à l’analyse du code managé, avertissements liés à la mobilité"
  - "avertissements liés à la mobilité"
  - "avertissements, mobilité"
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# Avertissements li&#233;s &#224; la mobilit&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les avertissements de mobilité prennent en charge la consommation d'énergie efficace.  
  
## Dans cette section  
  
|Règle|Description|  
|-----------|-----------------|  
|[CA1600 : Ne pas utiliser de priorité de processus inactif](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Ne définissez pas de priorité de processus inactif.  Sinon, les processus avec System.Diagnostics.ProcessPriorityClass.Idle occuperaient le processeur alors qu'il devrait être inactif et bloqueraient par conséquent la veille.|  
|[CA1601 : Ne pas utiliser de minuteries qui empêchent les changements d'état de l'alimentation](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|En effet, toute activité périodique supérieure à cette fréquence occupe le processeur et interfère avec les minuteries d'inactivité qui déclenchent la mise en veille de l'écran et des disques durs pour économiser de l'énergie.|