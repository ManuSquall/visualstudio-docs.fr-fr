---
title: 'DA0008 : Peu d’échantillons collectés | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: baf973837a687bb102dd857adf97caf0e1b8e5ab
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001772"
---
# <a name="da0008-few-samples-collected"></a>DA0008 : Peu d’échantillons collectés

|||  
|-|-|  
|ID de règle|DA0008|  
|Category|Utilisation des outils de profilage|  
|Méthode de profilage|Échantillonnage|  
|Message|Un petit nombre d’échantillons a été collecté. Augmentez la durée d’exécution ou utilisez un taux d’échantillonnage plus rapide pour des résultats plus significatifs.|  
|Type de règle|Information|  

## <a name="cause"></a>Cause  
 Seuls quelques échantillons ont été collectés pendant l’exécution du profilage.  

## <a name="rule-description"></a>Description de la règle  
 Lorsque la méthode d’échantillonnage est utilisée, vous devez collecter un nombre d’échantillons significatif du point de vue statistique pour vous assurer que les données reflètent bien le comportement réel du programme. Pour éviter les erreurs d’échantillonnage, essayez de collecter au moins 1 000 échantillons de comportements pour l’exécution des instructions du programme. Si vous ne collectez pas suffisamment d’échantillons, vous risquez de mal interpréter les données de profilage.  

## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour obtenir des résultats plus significatifs d’un point de vue statistique, effectuez le profilage d’une exécution d’application plus longue ou utilisez un taux d’échantillonnage plus rapide. Pour plus d’informations sur le changement du taux d’échantillonnage dans l’IDE de Visual Studio, consultez [Guide pratique pour choisir des événements d’échantillonnage](../profiling/how-to-choose-sampling-events.md). Pour plus d’informations sur la modification du taux d’échantillonnage lorsque vous utilisez la ligne de commande des outils de profilage, consultez [Timer](../profiling/timer.md) dans les informations de référence sur [VSPerfCmd](../profiling/vsperfcmd.md).