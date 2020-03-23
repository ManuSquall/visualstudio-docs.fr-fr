---
title: Collecte de données de concurrence de threads et de processus | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e8fda0300aad4a331366fac0a9ebd1b559cecc9d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779517"
---
# <a name="collect-thread-and-process-concurrency-data"></a>Collecter les données concurrentielles de threads et de processus

La méthode de profilage par concurrence des Outils de profilage de Visual Studio permet de collecter des données de contention de ressources comprenant des informations sur chacun des événements de synchronisation à cause desquels une fonction de l’application profilée doit attendre l’accès à une ressource.

Vous pouvez spécifier la méthode de profilage d’accès concurrentiel à l’aide de l’une des procédures suivantes :

- Dans la première page de l’Assistant Profilage, cliquez sur **Concurrence**.
- Dans la page **Général** de la boîte de dialogue Propriétés de la session de performance, cliquez sur **Concurrence**.
- Dans la barre d’outils de **l’Explorateur de performances**, dans la liste **Méthode**, cliquez sur **Concurrence**.

## <a name="common-tasks"></a>Tâches courantes

Vous pouvez spécifier des options supplémentaires dans la boîte de dialogue des _pages de propriétés_**session de performance** . Pour ouvrir la boîte de dialogue :

- Dans **Performance Explorer**, cliquez à droite sur le nom de la session de performance, puis cliquez sur **Properties**.

Les tâches du tableau suivant décrivent les options que vous pouvez spécifier dans la boîte de dialogue _Session de performance_**Pages de propriétés** quand vous effectuez un profilage à l’aide de la méthode d’accès concurrentiel.

|Tâche|Contenu associé|
|----------|---------------------|
|Dans la page **Général**, spécifiez les détails d’affectation de noms pour le fichier de données de profilage (.vsp) généré.|- [Comment : Définir les options de nom de fichier de données de performance](../profiling/how-to-set-performance-data-file-name-options.md)|
|Si votre solution de code contient plusieurs projets .exe, dans la page **Lancer**, spécifiez l’application à démarrer.|- [Comment: Spécifier le binaire pour commencer](../profiling/how-to-specify-the-binary-to-start.md)|
|Dans la page **Interaction de couche** , ajoutez les données d’appel ADO.NET à l’exécution du profilage.|- [Recueillir des données d’interaction de niveau](../profiling/collecting-tier-interaction-data.md)|
|Dans la page **Compteurs Windows** , spécifiez un ou plusieurs compteurs de performance de système d’exploitation à ajouter aux données de profilage en tant que marques.|- [Comment : Collecter des données de compteur Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Sur la page **Advanced,** spécifiez la version du délai d’exécution .NET Framework pour profiler si vos modules d’application utilisent plusieurs versions. Par défaut, la première version chargée est profilée.|- [Comment: Spécifier le temps d’exécution .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
