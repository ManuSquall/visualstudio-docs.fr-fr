---
title: 'DA0026 : Traitement du temps processeur noyau excessif | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fef0a3c42be1057bd1217ec676ae43b220d80345
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54768969"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026 : traitement du temps processeur noyau excessif
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id de règle | TODO |  
| Catégorie | Utilisation des outils de profilage |  
| Méthode de profilage | Échantillonnage |  
| Message | Un volume relativement élevé de temps CPU en mode de noyau a été mesuré. Analysez la source en activant l’échantillonnage de SysCall.|  
| Type de règle | Informations |  
  
 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## <a name="cause"></a>Cause  
 Le temps processeur qui a été exécuté en mode noyau a dépassé le temps passé en mode utilisateur. Effectuez de nouveau un profilage et un échantillonnage du nombre d’appels système (syscalls) pour déterminer la cause des durées élevées d’exécution en mode noyau.  
  
## <a name="rule-description"></a>Description de la règle  
 La proportion relativement élevée de temps passé par l’application en mode noyau peut nécessiter un examen approfondi. Une application en mode utilisateur passe en mode noyau pour effectuer des opérations d’E/S, pour attendre des primitives de synchronisation de thread ou de processus, ou pour effectuer des appels système. Vous pouvez rechercher les types d’appels système qu’émet l’application, ainsi que les fonctions qui sont responsables de ces appels quand vous sélectionnez l’option permettant de rassembler des échantillons de piles d’appels basés sur les appels système.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour rechercher les types d’appels système qu’émet votre application, exécutez de nouveau le profil et sélectionnez l’option permettant de rassembler des échantillons en fonction des appels système. Si vous exécutez les outils de profilage dans l’IDE, consultez [Guide pratique pour choisir des événements d’échantillonnage](../profiling/how-to-choose-sampling-events.md) pour plus d’informations. Si vous exécutez les outils de profilage à partir de la ligne de commande, consultez la section **Options d’intervalle d’échantillonnage** de la rubrique [VSPerfCmd](../profiling/vsperfcmd.md) dans la documentation de référence sur les outils en ligne de commande des outils de profilage.
