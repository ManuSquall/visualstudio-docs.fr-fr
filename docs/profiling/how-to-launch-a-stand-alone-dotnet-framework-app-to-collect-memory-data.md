---
title: 'Procédure : Lancer une application .NET Framework autonome avec le profileur pour collecter des données de mémoire en ligne de commande | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 18e90e44da8b36dbc4824817c7f13bbe423a2c12
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614179"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line"></a>Procédure : Lancer une application .NET Framework autonome avec le profileur pour collecter des données de mémoire en ligne de commande
Cette rubrique explique comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour démarrer une application autonome (cliente) .NET Framework et collecter des données de mémoire.

 Une session de profilage est constituée de trois parties :

-   Le démarrage de l’application à l’aide du profileur

-   La collecte des données de profilage

-   La fin de la session de profilage

> [!NOTE]
>  Pour obtenir le chemin d’accès des outils de profilage, voir [Spécifier le chemin d’accès des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

## <a name="start-the-application-with-the-profiler"></a>Démarrer l’application avec le profileur
 Pour démarrer une application cible à l’aide du profileur, utilisez les options **/start** et **/launch** de VSPerfCmd.exe pour initialiser le profileur et démarrer l’application. Vous pouvez spécifier **/start** et **/launch** et leurs options respectives sur une même ligne de commande.

 Vous pouvez également ajouter l’option **/globaloff** pour suspendre la collecte des données au démarrage de l’application cible. Ensuite, utilisez **/globalon** pour commencer à collecter les données.

#### <a name="to-start-an-application-by-using-the-profiler"></a>Pour démarrer une application à l’aide du profileur

1. Ouvrez une fenêtre Invite de commandes.

2. Démarrez le profileur. Type :

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - L’option [/start](../profiling/start.md)**:sample** initialise le profileur.

   - L’option [/output](../profiling/output.md)**:**`OutputFile` est nécessaire avec **/start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:sample**.

   | Option | Description |
   | - | - |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/automark](../profiling/automark.md) **:** `Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |


3. Démarrez l’application cible. Type :

    **VSPerfCmd**  [/launch](../profiling/launch.md) **:** `appName` **/gc:**{**allocation**&#124;**lifetime**}[`Options`]

   - L’option [/gc](../profiling/gc-vsperfcmd.md)**:**`Keyword` est nécessaire pour collecter les données de mémoire .NET Framework. Le paramètre de mot clé spécifie s’il faut collecter les données d’allocation de mémoire, ou collecter à la fois les données d’allocation de mémoire et les données de durée de vie des objets.

     |Mot clé|Description|
     |-------------|-----------------|
     |**allocation**|Collecter les données d’allocation de mémoire uniquement.|
     |**lifetime**|Collecte à la fois les données d’allocation de mémoire et les données de durée de vie des objets.|

     Vous pouvez utiliser l’une des options suivantes avec l’option **/launch**.

   |Option|Description|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:** `Arguments`|Spécifie une chaîne qui contient les arguments de ligne de commande à passer à l’application cible.|
   |[/console](../profiling/console.md)|Démarre l’application en ligne de commande cible dans une fenêtre distincte.|
   |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl).|
   |[/targetclr](../profiling/targetclr.md) **:** `Version`|Spécifie la version du common language runtime (CLR) à profiler lorsque plusieurs versions du runtime sont chargées dans une application.|

## <a name="control-data-collection"></a>Contrôler la collecte des données
 Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier à l’aide des options de *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

-   Les paires d’options suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/processon](../profiling/processon-and-processoff.md)  **:** `PID` [processoff](../profiling/processon-and-processoff.md)  **:** `PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|
    |[/attach](../profiling/attach.md) **:** `PID` [/detach](../profiling/detach.md)|**/attach** commence à collecter des données pour le processus spécifié par `PID` (l’ID du processus). **/detach** arrête la collecte des données pour tous les processus.|

-   Vous pouvez également utiliser l’option **VSPerfCmd.exe**[/mark](../profiling/mark.md) pour insérer une marque de profilage dans le fichier de données. La commande **/mark** ajoute un identificateur, un horodatage et une chaîne de texte facultative définie par l’utilisateur. Les marques peuvent servir à filtrer les données.

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage
 Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit plus être attaché à un processus profilé et doit être arrêté explicitement. Vous pouvez détacher le profileur d’une application profilée avec la méthode d’échantillonnage en fermant l’application ou en appelant l’option **VSPerfCmd /detach**. Vous devez alors appeler l’option **VSPerfCmd /shutdown** pour désactiver le profileur et fermer le fichier de données de profilage. La commande **VSPerfClrEnv /off** efface les variables d’environnement de profilage.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1.  Effectuez l’une des opérations suivantes pour détacher le profileur de l’application cible :

    -   Fermez l’application cible.

         - ou -

    -   Tapez **VSPerfCmd /detach**

2.  Fermez le profileur. Type :

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Voir aussi
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Vues des données de la mémoire .NET](../profiling/dotnet-memory-data-views.md)