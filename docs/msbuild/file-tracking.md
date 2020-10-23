---
title: Suivi des fichiers | Microsoft Docs
description: Utilisez les fonctions de suivi de fichier MSBuild pour consigner les appels au système de fichiers Windows pour un processus et ses processus enfants.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2fafae7cce22cc41fdd51a4bc727ac6bfb791b9
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436633"
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
