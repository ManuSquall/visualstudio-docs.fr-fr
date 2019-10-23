---
title: avertissements liés à la mobilité
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8dedf24f2f6615ec8d24faa0c1e6bc5a48dc2f05
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649211"
---
# <a name="mobility-warnings"></a>avertissements liés à la mobilité
Les avertissements relatifs à la mobilité prennent en charge l’efficacité énergétique.

## <a name="in-this-section"></a>Dans cette section

|Règle|Description|
|----------|-----------------|
|[CA1600 : N’utilisez pas la priorité de processus inactif ](../code-quality/ca1600.md)|N'affectez pas la valeur Idle à la priorité de processus. Sinon, les processus avec System.Diagnostics.ProcessPriorityClass.Idle occuperaient le processeur alors qu'il devrait être inactif et bloqueraient par conséquent la veille.|
|[CA1601 : N’utilisez pas de minuteries qui empêchent les modifications de l’état d’alimentation ](../code-quality/ca1601.md)|En effet, toute activité périodique supérieure à cette fréquence occupe le processeur et interfère avec les minuteries d'inactivité qui déclenchent la mise en veille de l'écran et des disques durs pour économiser de l'énergie.|
