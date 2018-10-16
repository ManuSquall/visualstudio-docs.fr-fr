---
title: 'DA0029 : version CLR non prise en charge | Microsoft Docs'
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
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6334fc69607f6d39e75d20c3b3ca228507db169d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265113"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029 : version CLR non prise en charge
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id de règle | DA0029 |  
| Catégorie | Utilisation des outils de profilage |  
| Méthode de profilage | Profilage à partir de la ligne de commande |  
| Message | Une version CLR non pris en charge a été détectée au cours de la collection. Les symboles managés ne peuvent pas être résolus correctement. |  
| Type de règle | Plus d’informations. |  
  
## <a name="cause"></a>Cause  
 Vous essayez de profiler une application qui utilise le [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)], qui n’est pas pris en charge par les Outils de profilage.  
  
## <a name="rule-description"></a>Description de la règle  
 Cet avertissement se produit car les Outils de profilage ne pourront pas résoudre les symboles du code managé qui s’exécute dans l’application. Les Outils de profilage ne peuvent pas résoudre les symboles du code managé pour les applications qui exécutent le [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)].  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Aucun.



