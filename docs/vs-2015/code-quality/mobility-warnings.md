---
title: Avertissements de mobilité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e67be4e501cb2d0dd9d584250fcea91af13fe657
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201249"
---
# <a name="mobility-warnings"></a>avertissements liés à la mobilité
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avertissements de mobilité prennent en charge la consommation d’énergie efficace.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Règle|Description|  
|----------|-----------------|  
|[CA1600 : N’utilisez pas de priorité de processus inactif](../code-quality/ca1600-do-not-use-idle-process-priority.md)|N'affectez pas la valeur Idle à la priorité de processus. Sinon, les processus avec System.Diagnostics.ProcessPriorityClass.Idle occuperaient le processeur alors qu'il devrait être inactif et bloqueraient par conséquent la veille.|  
|[CA1601 : Ne pas utiliser de minuteries qui empêchent les changements d’état d’alimentation](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|En effet, toute activité périodique supérieure à cette fréquence occupe le processeur et interfère avec les minuteries d'inactivité qui déclenchent la mise en veille de l'écran et des disques durs pour économiser de l'énergie.|
