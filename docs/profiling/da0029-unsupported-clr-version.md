---
title: DA0029-version CLR non prise en charge | Microsoft Docs
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
ms.openlocfilehash: 18cf60804e65f2cb67f74c5739a879a633043778
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936611"
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
