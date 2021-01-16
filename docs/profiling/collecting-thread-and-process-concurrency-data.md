---
title: Collecter les données de concurrence du processus de & de thread
description: Utilisez la Outils de profilage méthode de profilage d’accès concurrentiel pour collecter des données sur chaque événement de synchronisation qui amène une fonction à attendre l’accès aux ressources.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c1f6d0dbc8c10c972957e2bcf8092d145bb3651c
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533743"
---
# <a name="collect-thread-and-process-concurrency-data"></a>Collecter les données concurrentielles de threads et de processus

La méthode de profilage par concurrence des Outils de profilage de Visual Studio permet de collecter des données de contention de ressources comprenant des informations sur chacun des événements de synchronisation à cause desquels une fonction de l’application profilée doit attendre l’accès à une ressource.

Vous pouvez spécifier la méthode de profilage d’accès concurrentiel à l’aide de l’une des procédures suivantes :

- Dans la première page de l’Assistant Profilage, cliquez sur **Concurrence**.
- Dans la page **Général** de la boîte de dialogue Propriétés de la session de performance, cliquez sur **Concurrence**.
- Dans la barre d’outils de **l’Explorateur de performances**, dans la liste **Méthode**, cliquez sur **Concurrence**.

## <a name="common-tasks"></a>Tâches courantes

Vous pouvez spécifier des options supplémentaires dans la boîte de dialogue des _pages de propriétés_**session de performance** . Pour ouvrir la boîte de dialogue :

- Dans **Explorateur de performances**, cliquez avec le bouton droit sur le nom de la session de performance, puis cliquez sur **Propriétés**.

Les tâches du tableau suivant décrivent les options que vous pouvez spécifier dans la boîte de dialogue _Session de performance_**Pages de propriétés** quand vous effectuez un profilage à l’aide de la méthode d’accès concurrentiel.

|Tâche|Contenu associé|
|----------|---------------------|
|Dans la page **Général**, spécifiez les détails d’affectation de noms pour le fichier de données de profilage (.vsp) généré.|- [Procédure : définir les options de nom de fichier de données de performances](../profiling/how-to-set-performance-data-file-name-options.md)|
|Si votre solution de code contient plusieurs projets .exe, dans la page **Lancer**, spécifiez l’application à démarrer.|- [Comment : spécifier le binaire à démarrer](../profiling/how-to-specify-the-binary-to-start.md)|
|Dans la page **Interaction de couche** , ajoutez les données d’appel ADO.NET à l’exécution du profilage.|- [Collecter les données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)|
|Dans la page **Compteurs Windows** , spécifiez un ou plusieurs compteurs de performance de système d’exploitation à ajouter aux données de profilage en tant que marques.|- [Comment : collecter les données des compteurs Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Dans la page **avancé** , spécifiez la version du .NET Framework au moment de l’exécution pour le profilage si vos modules d’application utilisent plusieurs versions. Par défaut, la première version chargée est profilée.|- [Comment : spécifier le Runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
