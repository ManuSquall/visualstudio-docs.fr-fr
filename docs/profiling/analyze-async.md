---
title: Analyser les performances du code .NET Asynchronous | Microsoft Docs
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- asynchronous, async, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 49091ba472637d480c04c39f0170c2aee00595d2
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290419"
---
# <a name="analyze-performance-of-net-asynchronous-code"></a>Analyser les performances du code asynchrone .NET

Utilisez l’outil .NET Async pour analyser les performances du code asynchrone dans votre application.

> [!NOTE]
> L’outil .NET Async nécessite Visual Studio 2019 version 16,7 ou ultérieure et un projet .NET qui utilise **Async** et **await**.

## <a name="setup"></a>Programme d’installation

1. Appuyez sur **ALT + F2** pour ouvrir le profileur de performances dans Visual Studio.

1. Activez la case à cocher **.net Async** .

   ![Outil .NET Async sélectionné](../profiling/media/async-tool-selected.png "Outil .NET Async sélectionné")

1. Cliquez sur le bouton **Démarrer** pour exécuter l’outil.

1. Une fois l’exécution de l’outil terminée, parcourez le scénario que vous souhaitez profiler dans votre application. Sélectionnez ensuite **arrêter la collecte** ou fermez votre application pour afficher vos données.

1. Après l’arrêt de la collection, vous voyez un tableau des activités qui se sont produites lors de votre session de profilage.

   ![L’outil .NET Async s’est arrêté](../profiling/media/async-tool-opened.png "L’outil .NET Async s’est arrêté")

Les événements asynchrones sont organisés par ordre chronologique. Chaque affiche l’heure de début, l’heure de fin et la durée.

Chaque ligne qui correspond à une [tâche](https://docs.microsoft.com/dotnet/api/system.threading.tasks) est étiquetée dans la colonne **nom** . Pour tout nom de tâche qui ne peut pas être résolu, une **tâche dans** étiquette s’affiche. Il est suivi du nom de la méthode dans laquelle la tâche se produit. Si une activité asynchrone ne se termine pas dans la session de collecte, une étiquette **incomplète** apparaît dans la colonne **heure de fin** .

Pour approfondir l’étude d’une tâche ou d’une activité spécifique, cliquez avec le bouton droit sur la ligne. Sélectionnez ensuite **atteindre le fichier source** pour voir à quel endroit de votre code l’activité s’est produite.

![Outil .NET Async avec accéder au fichier source sélectionné](../profiling/media/async-tool-gotosource.png "Outil .NET Async avec accéder au fichier source sélectionné")

## <a name="see-also"></a>Voir aussi

- [Optimisation des paramètres du profileur](../profiling/optimize-profiler-settings.md)
