---
title: 'DA0029 : version CLR non prise en charge | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f6ab40efbba692cfa85f14b750d3c853d1112704
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765737"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029 : version CLR non prise en charge
|||  
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