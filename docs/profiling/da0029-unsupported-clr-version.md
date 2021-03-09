---
title: DA0029-version CLR non prise en charge | Microsoft Docs
description: Vous essayez de profiler une application qui utilise le .NET Framework 1,1 qui n’est pas pris en charge par le Outils de profilage.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b3f5e5129bed479273e141af70121d5a344972e2
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465840"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029 : version CLR non prise en charge

|Élément|Valeur|
|-|-|
|ID de règle|DA0029|
|Category|Utilisation des outils de profilage|
|Méthode de profilage|Profilage à partir de la ligne de commande|
|Message|Une version CLR non prise en charge a été détectée lors de la collection. Les symboles managés peuvent ne pas être résolus correctement.|
|Type de règle|Information.|

## <a name="cause"></a>Cause
 Vous essayez de profiler une application qui utilise le [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)], qui n’est pas pris en charge par les Outils de profilage.

## <a name="rule-description"></a>Description de la règle
 Cet avertissement se produit car les Outils de profilage ne pourront pas résoudre les symboles du code managé qui s’exécute dans l’application. Les Outils de profilage ne peuvent pas résoudre les symboles du code managé pour les applications qui exécutent le [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Aucun.
