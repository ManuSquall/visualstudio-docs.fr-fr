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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6061b614442d7bcb2f3465b1c40f35d583626c45
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78167583"
---
# <a name="mobility-warnings"></a>avertissements liés à la mobilité
Les avertissements relatifs à la mobilité prennent en charge l’efficacité énergétique.

## <a name="in-this-section"></a>Dans cette section

|Règle|Description|
|----------|-----------------|
|[CA1600 : N’utilisez pas de priorité de processus inactif](../code-quality/ca1600.md)|N'affectez pas la valeur Idle à la priorité de processus. Sinon, les processus avec System.Diagnostics.ProcessPriorityClass.Idle occuperaient le processeur alors qu'il devrait être inactif et bloqueraient par conséquent la veille.|
|[CA1601 : Ne pas utiliser de minuteries qui empêchent les changements d’état de l’alimentation](../code-quality/ca1601.md)|En effet, toute activité périodique supérieure à cette fréquence occupe le processeur et interfère avec les minuteries d'inactivité qui déclenchent la mise en veille de l'écran et des disques durs pour économiser de l'énergie.|
