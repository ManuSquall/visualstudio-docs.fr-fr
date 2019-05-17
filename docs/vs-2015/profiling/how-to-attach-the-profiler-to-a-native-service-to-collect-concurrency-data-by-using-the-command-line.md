---
title: 'Procédure : attacher le profileur à un service natif pour collecter des données concurrentielles en utilisant la ligne de commande | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab6e56d6b2d9a953b5549d59ea85049be8cc0306
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432885"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line"></a>Procédure : Attacher le Profiler à un Service natif pour collecter des données concurrentielles en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique explique comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour attacher le profileur à un service natif (C/C++) et pour collecter des données de concurrence de processus et de threads à l’aide de la méthode d’échantillonnage.  

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications Windows Store demandent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
> Les outils en ligne de commande des outils de profilage se trouvent dans le sous-répertoire \Team Tools\Performance Tools du répertoire d’installation Visual Studio. Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser le profileur dans une fenêtre d’invite de commandes, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’**invite de commandes**, ou l’ajouter à la commande. Pour plus d’informations, consultez [Spécification du chemin d’accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Lorsque le profileur est attaché au service, vous pouvez suspendre et reprendre la collecte de données. Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit plus être attaché au service et doit être arrêté explicitement.  

## <a name="attaching-the-profiler"></a>Attachement du profileur  
 Pour attacher le profileur à un service natif, utilisez les options **VSPerfCmd/start** et **/attach** pour initialiser le profileur et l’attacher à l’application cible. Vous pouvez spécifier **/start** et **/attach** et leurs options respectives sur une même ligne de commande. Vous pouvez également ajouter l’option **/globaloff** pour suspendre la collecte des données au démarrage de l’application cible. Ensuite, utilisez **/globalon** pour commencer à collecter les données.  

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Pour attacher le profileur à un service natif  

1. Si le service n’est pas en cours d’exécution, démarrez-le.  

2. Démarrez le profileur en tapant ce qui suit à l’invite de commandes :  

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency   /output:** `OutputFile` [`Options`]  

   - L’option [/output](../profiling/output.md)**:**`OutputFile` est nécessaire avec **/start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).  

     Vous pouvez utiliser l’une des options du tableau suivant avec l’option **/start**.  

   > [!NOTE]
   > La plupart des services nécessitent les options **/user** et **/crosssession**.  

   |                               Option                               |                                                                     Description                                                                      |
   |--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`UserName` |                           Spécifie les noms de domaine et d’utilisateur facultatifs du compte qui doit obtenir l’accès au profileur.                           |
   |           [/crosssession](../profiling/crosssession.md)            |                                               Active le profilage des processus dans d’autres sessions ouvertes.                                                |
   |  [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`  |                                      Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage.                                       |
   |       [/automark](../profiling/automark.md) **:** `Interval`       | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   |     [/events](../profiling/events-vsperfcmd.md) **:** `Config`     |       Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl).       |

3. Attachez le profileur au service en tapant la commande suivante dans la fenêtre d’invite de commandes :  

    **VSPerfCmd /attach:** `PID`  

    `PID` spécifie l’ID ou le nom de processus de l’application cible. Vous pouvez afficher les ID de processus de tous les processus en cours d’exécution dans le gestionnaire des tâches de Windows.  

## <a name="controlling-data-collection"></a>Contrôle de la collection de données  
 Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier à l’aide des options de VSPerfCmd.exe. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.  

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données  

- Les paires d’options du tableau suivant permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  

    |Option|Description|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** commence à collecter des données pour le processus spécifié par l’ID de processus (`PID`) ou le nom de processus (*ProcName*). **/detach** arrête la collecte des données pour le processus spécifié ou pour tous les processus, si aucun processus n’est spécifié.|  

## <a name="ending-the-profiling-session"></a>Fin d’une session de profilage  
 Pour mettre fin à une session de profilage, le profileur ne doit pas être en train de collecter des données. Vous pouvez arrêter la collecte des données d’un service natif profilé avec la méthode d’accès concurrentiel en arrêtant le service ou en appelant l’option **VSPerfCmd /detach**. Vous devez alors appeler l’option **VSPerfCmd /shutdown** pour désactiver le profileur et fermer le fichier de données de profilage.  

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage  

1. Détachez le profileur de l’application cible en arrêtant le service ou en tapant la commande suivante dans la fenêtre d’invite de commandes :  

     Tapez **VSPerfCmd /detach**  

2. Fermez le profileur en tapant ce qui suit à l’invite de commandes :  

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)
