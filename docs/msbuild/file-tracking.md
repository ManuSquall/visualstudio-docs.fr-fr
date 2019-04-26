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
ms.openlocfilehash: 7770da734143b2b6185b266137eeb46ba25bd32a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968065"
---
# <a name="file-tracking"></a>Suivi des fichiers
Le suivi des fichiers journalise les appels au système de fichiers Windows pour un processus et ses processus enfants. En appelant les fonctions listées ci-dessous, les programmes contrôlent le moment auquel activer et désactiver la journalisation, et spécifient le fichier journal à utiliser.

- [EndTrackingContext](../msbuild/endtrackingcontext.md) Arrête le suivi dans le contexte actuel.

- [ResumeTracking](../msbuild/resumetracking.md) Redémarre le suivi après un appel à [SuspendTracking](../msbuild/suspendtracking.md).

- [SetThreadCount](../msbuild/setthreadcount.md) Définit le nombre de threads à utiliser pour le suivi.

- [StartTrackingContext](../msbuild/starttrackingcontext.md) Démarre un nouveau contexte de suivi.

- [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md) Démarre un nouveau contexte de suivi avec une racine spécifique.

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) Met fin au suivi et libère les ressources utilisées.

- [SuspendTracking](../msbuild/suspendtracking.md) Interrompt temporairement le suivi.

- [WriteAllTLogs](../msbuild/writealltlogs.md) Écrit les journaux de suivi pour tous les contextes.

- [WriteContextTLogs](../msbuild/writecontexttlogs.md) Écrit le journal de suivi pour le contexte actuel.