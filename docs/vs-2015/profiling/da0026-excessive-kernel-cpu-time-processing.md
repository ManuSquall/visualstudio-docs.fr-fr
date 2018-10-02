---
title: 'DA0026 : Traitement du temps processeur noyau excessif | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29eda10403e2d09f5a1bdf67911e1f2ae58bd9f0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501205"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026 : traitement du temps processeur noyau excessif
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [DA0026 : traitement du temps processeur noyau excessif](https://docs.microsoft.com/visualstudio/profiling/da0026-excessive-kernel-cpu-time-processing).  
  
Id de règle | TODO |  
| Catégorie | Utilisation des outils de profilage |  
| Méthode de profilage | Échantillonnage |  
| Message | Un volume relativement élevé de temps CPU en mode de noyau a été mesuré. Analysez la source de l’échantillonnage de SysCall. |  
| Type de règle | Informations |  
  
 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## <a name="cause"></a>Cause  
 Le temps processeur qui a été exécuté en mode noyau a dépassé le temps passé en mode utilisateur. Effectuez de nouveau un profilage et un échantillonnage du nombre d’appels système (syscalls) pour déterminer la cause des durées élevées d’exécution en mode noyau.  
  
## <a name="rule-description"></a>Description de la règle  
 La proportion relativement élevée de temps passé par l’application en mode noyau peut nécessiter un examen approfondi. Une application en mode utilisateur passe en mode noyau pour effectuer des opérations d’E/S, pour attendre des primitives de synchronisation de thread ou de processus, ou pour effectuer des appels système. Vous pouvez rechercher les types d’appels système qu’émet l’application, ainsi que les fonctions qui sont responsables de ces appels quand vous sélectionnez l’option permettant de rassembler des échantillons de piles d’appels basés sur les appels système.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour rechercher les types d’appels système qu’émet votre application, exécutez de nouveau le profil et sélectionnez l’option permettant de rassembler des échantillons en fonction des appels système. Si vous exécutez les outils de profilage dans l’IDE, consultez [Guide pratique pour choisir des événements d’échantillonnage](../profiling/how-to-choose-sampling-events.md) pour plus d’informations. Si vous exécutez les outils de profilage à partir de la ligne de commande, consultez la section **Options d’intervalle d’échantillonnage** de la rubrique [VSPerfCmd](../profiling/vsperfcmd.md) dans la documentation de référence sur les outils en ligne de commande des outils de profilage.



