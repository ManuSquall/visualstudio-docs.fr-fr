---
title: 'DA0008 : Peu d’échantillons collectés | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6e294c03f958259f26938865a3e26c6fb7669d6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289807"
---
# <a name="da0008-few-samples-collected"></a>DA0008 : Peu d'échantillons collectés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id de règle | DA0008 |  
| Catégorie | Utilisation des outils de profilage |  
| Méthode de profilage | Échantillonnage |  
| Message | Seuls quelques échantillons ont été collectés. Envisagez un taux d’échantillonnage d’exécution ou plus rapide de plus de temps pour des résultats plus significatifs. |  
| Type de règle | Informations |  
  
## <a name="cause"></a>Cause  
 Seuls quelques échantillons ont été collectés pendant l’exécution du profilage.  
  
## <a name="rule-description"></a>Description de la règle  
 Lorsque la méthode d’échantillonnage est utilisée, vous devez collecter un nombre d’échantillons significatif du point de vue statistique pour vous assurer que les données reflètent bien le comportement réel du programme. Pour éviter les erreurs d’échantillonnage, essayez de collecter au moins 1 000 échantillons de comportements pour l’exécution des instructions du programme. Si vous ne collectez pas suffisamment d’échantillons, vous risquez de mal interpréter les données de profilage.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour obtenir des résultats plus significatifs d’un point de vue statistique, effectuez le profilage d’une exécution d’application plus longue ou utilisez un taux d’échantillonnage plus rapide. Pour plus d’informations sur la modification du taux d’échantillonnage dans l’IDE de Visual Studio, consultez [Guide pratique pour choisir des événements d’échantillonnage](../profiling/how-to-choose-sampling-events.md). Pour plus d’informations sur la modification du taux d’échantillonnage lorsque vous utilisez la ligne de commande des outils de profilage, consultez [Timer](../profiling/timer.md) dans les informations de référence sur [VSPerfCmd](../profiling/vsperfcmd.md).



