---
title: 'Ligne de commande du profileur : ouvrir l’application cliente .NET, accéder aux données d’accès concurrentiel'
description: Découvrez comment utiliser les outils en ligne de commande de Visual Studio Outils de profilage pour démarrer une application autonome .NET et collecter des données de concurrence de processus et de threads.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 01356e2fe8693e39ef06fc1620cabbb2cb608a43
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883455"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Guide pratique pour lancer une application .NET Framework autonome avec le profileur pour collecter des données d’accès concurrentiel en utilisant la ligne de commande
Cette rubrique explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour démarrer une application .NET Framework autonome (cliente) et pour collecter des données de concurrence de processus et de threads

> [!NOTE]
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

 Lorsque le profileur est attaché à l’application, vous pouvez suspendre et reprendre la collecte de données. Pour terminer une session de profilage, le profileur ne doit plus être attaché à l’application et doit être arrêté explicitement.

## <a name="start-the-application-with-the-profiler"></a>Démarrer l’application avec le profileur
 Pour lancer une application cible .NET Framework avec le profileur, utilisez *VSPerfClrEnv.exe* pour définir les variables de profilage .NET Framework. Vous utilisez ensuite les options **/start** et **/launch** de VSPerfCmd pour initialiser le profileur et démarrer l’application. Vous pouvez spécifier **/start** et **/launch** et leurs options respectives sur une même ligne de commande. Vous pouvez également ajouter l’option **/globaloff** à la ligne de commande pour suspendre la collecte des données au démarrage de l’application cible. Vous utilisez ensuite **/globalon** sur une ligne de commande séparée pour commencer à collecter les données.

#### <a name="to-start-an-application-with-the-profiler"></a>Pour démarrer une application à l’aide du profileur

1. Ouvrir une fenêtre d’invite de commandes.

2. Démarrez le profileur. Tapez :

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**[**,**{**ResourceOnly**&#124;**ThreadOnly**}] **/output:**`OutputFile` [`Options`]

   - L’option [/start](../profiling/start.md) initialise le profileur.

     | | |
     |-------------------------------------| - |
     | **/start:concurrency** | Active la collecte de données relatives aux conflits de ressources et à l’exécution des threads. |
     | **/start:concurrency,resourceonly** | Active la collecte de données relatives aux conflits de ressources uniquement. |
     | **/start:concurrency,threadonly** | Active la collecte de données relatives à l’exécution des threads uniquement. |

   - L’option [/Output](../profiling/output.md)**:** `OutputFile` est requise avec **/Start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:concurrency**.

   | Option | Description |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `domain\` ]`username` | Spécifie les noms de domaine et d’utilisateur facultatifs du compte qui doit obtenir l’accès au profileur. |
   | [/CrossSession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions ouvertes. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un (.*fichier ETL*). |

3. Démarrez l’application cible. Tapez :

    **VSPerfCmd**  [/Launch](../profiling/launch.md) **:** `AppName` [ `Options` ] [ `Sample Event` ]

    Vous pouvez utiliser l’une des options suivantes avec l’option **/launch**.

   |Option|Description|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Spécifie une chaîne qui contient les arguments de ligne de commande à passer à l’application cible.|
   |[/Console](../profiling/console.md)|Démarre l’application en ligne de commande cible dans une fenêtre distincte.|
   |[/TargetCLR](../profiling/targetclr.md) **:**`Version`|Spécifie la version du common language runtime (CLR) à profiler lorsque plusieurs versions du runtime sont chargées dans une application.|

## <a name="control-data-collection"></a>Contrôler la collecte des données
 Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier à l’aide des options de *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

1. Les paires d’options suivantes de *VSPerfCmd.exe* démarrent et arrêtent la collecte de données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach** commence à collecter des données pour le processus spécifié par l’ID de processus (`PID`) ou le nom de processus (ProcName). **/Detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus spécifique n’est spécifié.|

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage
 Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit pas être en train de collecter des données. Vous pouvez arrêter la collecte des données concurrentielles en fermant l’application profilée ou en appelant l’option **VSPerfCmd /detach**. Vous devez alors appeler l’option **VSPerfCmd /shutdown** pour désactiver le profileur et fermer le fichier de données de profilage. La commande **VSPerfClrEnv /off** efface les variables d’environnement de profilage.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Effectuez l’une des opérations suivantes pour détacher le profileur de l’application cible.

    - Fermez l’application cible.

         -ou-

    - Tapez **VSPerfCmd/detach**

2. Fermez le profileur

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Voir aussi
- [Collecter les données d’accès concurrentiel](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)
