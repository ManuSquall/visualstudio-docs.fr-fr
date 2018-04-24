---
title: Suivi des fichiers | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51d17894025800acd9c8ab0736ebe92d7f790fc7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="file-tracking"></a>Suivi de fichier
Le suivi des fichiers journalise les appels au système de fichiers Windows pour un processus et ses processus enfants. En appelant les fonctions listées ci-dessous, les programmes contrôlent le moment auquel activer et désactiver la journalisation, et spécifient le fichier journal à utiliser.  
  
## <a name="in-this-section"></a>Dans cette section  
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