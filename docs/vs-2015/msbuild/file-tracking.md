---
title: Suivi des fichiers | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5afc245bd16954ba348b4ec581238bf17e5d994
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758711"
---
# <a name="file-tracking"></a>Suivi de fichier
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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
