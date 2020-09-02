---
title: 'DA0029 : version CLR non prise en charge | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 532427618f476e1e187d8a1c88749810f9d157c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152642"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029 : Version CLR non prise en charge
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID de règle | DA0029 |  
| Catégorie | Utilisation de Outils de profilage |  
| Méthode de profilage | Profilage à partir de la ligne de commande |  
| Message | Une version CLR non prise en charge a été détectée pendant la collection. Les symboles managés peuvent ne pas être résolus correctement.|  
| Type de règle | Informations. |  
  
## <a name="cause"></a>Cause :  
 Vous essayez de profiler une application qui utilise le [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)], qui n’est pas pris en charge par les Outils de profilage.  
  
## <a name="rule-description"></a>Description de la règle  
 Cet avertissement se produit car les Outils de profilage ne pourront pas résoudre les symboles du code managé qui s’exécute dans l’application. Les Outils de profilage ne peuvent pas résoudre les symboles du code managé pour les applications qui exécutent le [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)].  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Aucun.
