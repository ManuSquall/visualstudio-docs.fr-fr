---
title: Attacher le profileur à une application native et collecter des données concurrentielles
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: dcc125f795a29f53abb07920aa11c9a5e6ee966b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85329520"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>Guide pratique pour attacher le profileur à une application autonome native et collecter des données de concurrence en utilisant la ligne de commande
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à une application native (C/C++) autonome en cours d’exécution et collecter des données sur les contentions de threads.

> [!NOTE]
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

 Lorsque le profileur est attaché à l’application, vous pouvez suspendre et reprendre la collecte de données. Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit plus être attaché à l’application et doit être arrêté explicitement.

## <a name="attach-the-profiler-to-a-running-native-application"></a>Attacher le profileur à une application native en cours d’exécution

#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>Pour attacher le profileur à une application native en cours d’exécution

1. Saisissez ensuite la commande suivante dans une invite de commandes :

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**

     Vous pouvez utiliser l’une des options du tableau suivant avec l’option **/start:concurrency**.

    |Option|Description|
    |------------|-----------------|
    |[/User](../profiling/user-vsperfcmd.md) **:**[ `Domain\` ]`Username`|Spécifie les noms de domaine et d’utilisateur facultatifs du compte qui doit obtenir l’accès au profileur.|
    |[/CrossSession](../profiling/crosssession.md)|Active le profilage des processus dans d’autres sessions ouvertes.|
    |[/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath`|Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage.|
    |[/AutoMark](../profiling/automark.md) **:**`Interval`|À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est 500.|
    |[/Events](../profiling/events-vsperfcmd.md) **:**`Config`|Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl).|

2. Attachez le profileur à l’application cible en tapant la commande suivante :

     **VSPerfCmd**  [/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` }

     `PID` spécifie l’ID de processus de l’application cible. Vous pouvez afficher les ID de processus de tous les processus en cours d’exécution dans le gestionnaire des tâches de Windows.

## <a name="control-data-collection"></a>Contrôler la collecte des données
 Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier à l’aide des options de *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

- Les paires d’options du tableau suivant permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach** commence à collecter des données pour le processus spécifié par l’ID de processus (`PID`) ou le nom de processus (*ProcName*). **/detach** arrête la collecte des données pour le processus spécifié ou pour tous les processus, si aucun processus n’est spécifié.|

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage
 Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit pas être en train de collecter des données. Vous pouvez arrêter la collecte des données d’une application profilée avec la méthode d’échantillonnage en fermant l’application ou en appelant l’option **VSPerfCmd /detach**. Vous devez alors appeler l’option **VSPerfCmd /shutdown** pour désactiver le profileur et fermer le fichier de données de profilage.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Détachez le profileur de l’application cible en fermant l’application ou en tapant la commande suivante :

     **VSPerfCmd /detach**

2. Fermez le profileur en tapant la commande suivante :

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)
