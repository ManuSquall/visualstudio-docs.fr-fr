---
title: Avertissements de mobilité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9833b4ef197419b8a20c3758bcc4dca71d1f10e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mobility-warnings"></a>avertissements liés à la mobilité
Avertissements de mobilité prennent en charge la consommation d’énergie efficace.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Règle|Description|  
|----------|-----------------|  
|[CA1600 : N’utilisez pas de priorité de processus inactif](../code-quality/ca1600-do-not-use-idle-process-priority.md)|N'affectez pas la valeur Idle à la priorité de processus. Sinon, les processus avec System.Diagnostics.ProcessPriorityClass.Idle occuperaient le processeur alors qu'il devrait être inactif et bloqueraient par conséquent la veille.|  
|[CA1601 : Ne pas utiliser de minuteries qui empêchent les changements d’état de l’alimentation](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|En effet, toute activité périodique supérieure à cette fréquence occupe le processeur et interfère avec les minuteries d'inactivité qui déclenchent la mise en veille de l'écran et des disques durs pour économiser de l'énergie.|