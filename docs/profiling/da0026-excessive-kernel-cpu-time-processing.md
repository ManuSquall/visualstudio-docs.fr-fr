---
title: 'DA0026 : Traitement temps CPU noyaux excessif | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 20abd86d12db44dac1a2b3a7772e90dee1b2721f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855453"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026 : Traitement temps CPU noyaux excessif

|||  
|-|-|  
|ID de règle|TODO|  
|Category|Utilisation des outils de profilage|  
|Méthode de profilage|Échantillonnage|  
|Message|Temps CPU en mode noyau relativement élevé. Analysez la source en activant l’échantillonnage de SysCall.|  
|Type de règle|Information|  

 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  

## <a name="cause"></a>Cause  
 Le temps processeur qui a été exécuté en mode noyau a dépassé le temps passé en mode utilisateur. Effectuez de nouveau un profilage et un échantillonnage du nombre d’appels système (syscalls) pour déterminer la cause des durées élevées d’exécution en mode noyau.  

## <a name="rule-description"></a>Description de la règle  
 La proportion relativement élevée de temps passé par l’application en mode noyau peut nécessiter un examen approfondi. Une application en mode utilisateur passe en mode noyau pour effectuer des opérations d’E/S, pour attendre des primitives de synchronisation de thread ou de processus, ou pour effectuer des appels système. Vous pouvez rechercher les types d’appels système qu’émet l’application, ainsi que les fonctions qui sont responsables de ces appels quand vous sélectionnez l’option permettant de rassembler des échantillons de piles d’appels basés sur les appels système.  

## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour rechercher les types d’appels système qu’émet votre application, exécutez de nouveau le profil et sélectionnez l’option permettant de rassembler des échantillons en fonction des appels système. Voir [Guide pratique pour choisir des événements d’échantillonnage](../profiling/how-to-choose-sampling-events.md) si vous exécutez les outils de profilage dans l’IDE. Si vous exécutez les outils de profilage à partir de la ligne de commande, consultez la section **Options d’intervalle d’échantillonnage** de l’article [VSPerfCmd](../profiling/vsperfcmd.md) dans la documentation de référence sur les outils en ligne de commande des outils de profilage.