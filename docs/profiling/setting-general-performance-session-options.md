---
title: "Définition des options générales d’une session de performances | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.general
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 36e27189102fbab8e698320c49bd008adf1eda50
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2018
---
# <a name="setting-general-performance-session-options"></a>Définition des options générales d'une session de performance

Vous pouvez définir la méthode de collecte et les conventions de nommage des données de profilage pour une session de performance des Outils de profilage de Visual Studio sur la page **Général** de la boîte de dialogue des propriétés de la session de performance. Pour ouvrir cette boîte de dialogue depuis **l’Explorateur de performances**, cliquez avec le bouton droit sur la session de performances, puis cliquez sur **Propriétés**.

## <a name="choosing-data-collection-methods"></a>Choix des méthodes de collecte de données

Vous définissez la méthode de collecte de base en sélectionnant une des options sous **Collecte du profilage**. Les options sont décrites dans le tableau suivant :

|||
|-|-|
|**Échantillonnage** La méthode d’échantillonnage collecte des informations de profilage à intervalles réguliers. Cette méthode est pratique pour détecter les problèmes d’utilisation du processeur ; il s’agit de la méthode recommandée pour commencer la plupart des investigations sur les performances.|- [Collecte de statistiques de performance à l’aide de l’échantillonnage](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**Instrumentation**. La méthode d’instrumentation injecte du code de profilage dans une copie d’un module, qui enregistre chaque entrée, sortie et appel de fonction des fonctions du module pendant une exécution du profilage. Cette méthode est pratique pour rassembler des informations chronologiques détaillées sur une section de votre code, et pour comprendre l’impact des opérations d’entrée et de sortie sur les performances de l’application.|- [Collecte de données de minutage détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**Concurrence** La méthode de concurrence collecte des données pour chaque événement qui bloque l’exécution de votre code, comme quand un thread attend que l’accès bloqué à une ressource de l’application soit libéré. Cette méthode est pratique pour l’analyse des applications multithreads.|- [Collecte de données de concurrence de threads et de processus](../profiling/collecting-thread-and-process-concurrency-data.md)|

 Vous pouvez collecter des données de mémoire .NET en utilisant les méthodes d’échantillonnage ou d’instrumentation. Vous sélectionnez le type de données sous **Profilage de mémoire .NET**.

|||
|-|-|
|**Collectez les informations d’allocation d’objets .NET**. Par défaut, les données incluent le nombre et la taille des objets alloués. Cochez ou décochez cette case pour activer ou désactiver la collecte de données mémoire .NET.<br /><br /> **Collecter aussi les informations de durée de vie des objets .NET**. Cochez cette case pour inclure des données sur les générations de garbage collection qui ont été utilisées pour récupérer les objets en mémoire.|- [Collecte des données liées à la durée de vie des objets et à l’allocation de mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|

 Une page de session de profilage apparaît quand vous commencez à profiler une application, où vous pouvez suspendre, reprendre et arrêter le profilage.

 ![Page de session de profilage](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="setting-profiling-data-file-options"></a>Définition des options des fichiers de données de profilage

|||
|-|-|
|**Rapport**. Par défaut, le nom du fichier de données de profilage (.vsp) est le nom de l’application profilée ; ce fichier se trouve dans le dossier de la solution ou du projet. Une chaîne de date est également ajoutée au nom ; en outre, un numéro incrémenté est ajouté aux fichiers de données qui sans cela auraient des noms en doublon. Vous pouvez modifier ces options.|- [Guide pratique pour définir les options de nom de fichier de données de profilage](../profiling/how-to-set-performance-data-file-name-options.md)|