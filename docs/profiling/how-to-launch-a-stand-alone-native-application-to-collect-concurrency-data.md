---
title: 'Ligne de commande du profileur : ouvrir une application cliente native, accéder aux données de concurrence'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb8baed0d9154c02f23738944de2d3e84b7402b
ms.sourcegitcommit: 0c3c4bd38455f7046c5c5a448eaaa5e407ad5bf4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76726033"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Guide pratique pour lancer une application native autonome avec le profileur pour collecter des données d’accès concurrentiel en utilisant la ligne de commande
Cette rubrique explique comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour démarrer une application autonome (cliente) native et pour collecter des données de concurrence de processus et de threads.

 Une session de profilage est constituée de trois parties :

- Le démarrage de l’application avec le profileur

- Le contrôle de la collecte de données

- La fin de la session de profilage

> [!NOTE]
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

## <a name="start-the-application-with-the-profiler"></a>Démarrer l’application avec le profileur
 Pour démarrer une application cible à l’aide du profileur, utilisez les options [/start](../profiling/vsperfcmd.md) et **/launch** de **VSPerfCmd.exe** pour initialiser le profileur et démarrer l’application. Vous pouvez spécifier **/start** et **/launch** et leurs options respectives. Vous pouvez également ajouter l’option **/globaloff** pour suspendre la collecte des données au démarrage de l’application cible. Ensuite, utilisez **/globalon** pour commencer à collecter les données.

#### <a name="to-start-an-application-with-the-profiler"></a>Pour démarrer une application à l’aide du profileur

1. À l'invite de commande, tapez la commande suivante :

     [VSPerfCmd](../profiling/vsperfcmd.md) **/Start : concurrence/output :** `OutputFile` [`Options`]

     L’option [/output](../profiling/output.md) **:** `OutputFile` est nécessaire avec **/start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).

     Vous pouvez utiliser l’une des options du tableau suivant avec l’option **/start:concurrency**.

    |Option|Description|
    |------------|-----------------|
    |[/WinCounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage.|
    |[/AutoMark](../profiling/automark.md) **:** `Interval`|À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms.|
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl).|

2. Démarrez l’application cible en tapant ce qui suit :

     **VSPerfCmd**  [/Launch](../profiling/launch.md) **:** `AppName` [`Options`]

     Vous pouvez utiliser l’une des options du tableau suivant avec l’option **/launch**.

    |Option|Description|
    |------------|-----------------|
    |[/args](../profiling/args.md) **:** `Arguments`|Spécifie une chaîne qui contient les arguments de ligne de commande à passer à l’application cible.|
    |[/console](../profiling/console.md)|Démarre l’application en ligne de commande cible dans une fenêtre distincte.|
    |[/TargetCLR](../profiling/targetclr.md) **:** `CLRVersion`|Spécifie la version du common language runtime (CLR) à profiler lorsque plusieurs versions du runtime sont chargées dans une application.|

## <a name="control-data-collection"></a>Contrôler la collecte des données
 Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l’écriture des données dans le fichier avec les options *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

- Les paires d’options du tableau suivant permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Démarre ( **/globalon**) ou arrête ( **/globaloff**) la collecte des données pour tous les processus.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|Démarre ( **/processon**) ou arrête ( **/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|
    |[/Attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/Detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/attach** commence à collecter des données pour le processus spécifié par l’ID de processus (`PID`) ou le nom de processus (*ProcName*). **/detach** arrête la collecte des données pour le processus spécifié ou pour tous les processus, si aucun processus n’est spécifié.|

- Vous pouvez également utiliser l’option **VSPerfCmd.exe**[/mark](../profiling/mark.md) pour insérer une marque de profilage dans le fichier de données. La commande **/mark** ajoute un identificateur, un horodatage et une chaîne de texte facultative définie par l’utilisateur. Les marques peuvent être utilisées pour filtrer les données des rapports et des vues de données du profileur.

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage
 Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit pas être en train de collecter des données. Vous pouvez arrêter la collecte des données concurrentielles en fermant l’application profilée ou en appelant l’option **VSPerfCmd /detach**. Vous devez alors appeler l’option **VSPerfCmd /shutdown** pour désactiver le profileur et fermer le fichier de données de profilage.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Détachez le profileur de l’application cible en fermant l’application ou en tapant la commande suivante à l’invite de commandes :

     **VSPerfCmd /detach**

2. Fermez le profileur en tapant ce qui suit à l’invite de commandes :

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)