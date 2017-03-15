---
title: "File Tracking | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, file tracking"
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# File Tracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le suivi de fichier permet d'enregistrer des appels dans le système de fichiers Windows pour un processus et ses processus enfants.  En appelant les fonctions répertoriées ci\-dessous, les programmes contrôlent le moment où il est nécessaire d'activer ou de désactiver cette enregistrement et de spécifier le fichier journal à utiliser.  
  
## Dans cette section  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Arrêtez le suivi du contexte actuel.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Reprenez le suivi après un appel à [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Définissez le nombre de threads à utiliser pour le suivi.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Commencez un nouveau contexte de suivi.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Commencez un nouveau contexte de suivi avec une racine spécifiée.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Terminez le suivi et libérez les ressources utilisées.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Interrompez temporairement le suivi.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Écrivez les journaux de suivi pour tous les contextes.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Écrivez le journal de suivi pour le contexte actuel.