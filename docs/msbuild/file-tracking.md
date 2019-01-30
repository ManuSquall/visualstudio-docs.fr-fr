---
title: Suivi des fichiers | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 878d4d7e56c51d8a41a0e3cf3e78d6c83ed5d0b5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027670"
---
# <a name="file-tracking"></a>Suivi des fichiers
Le suivi des fichiers journalise les appels au système de fichiers Windows pour un processus et ses processus enfants. En appelant les fonctions listées ci-dessous, les programmes contrôlent le moment auquel activer et désactiver la journalisation, et spécifient le fichier journal à utiliser.  
  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Arrête le suivi dans le contexte actuel.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Redémarre le suivi après un appel à [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Définit le nombre de threads à utiliser pour le suivi.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Démarre un nouveau contexte de suivi.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Démarre un nouveau contexte de suivi avec une racine spécifiée.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Termine le suivi et libère les ressources utilisées.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Suspend temporairement le suivi.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Écrit les journaux de suivi pour tous les contextes.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Écrit le journal de suivi du contexte actuel.