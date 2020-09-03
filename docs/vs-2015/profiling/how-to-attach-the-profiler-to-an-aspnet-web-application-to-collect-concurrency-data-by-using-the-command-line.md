---
title: Guide pratique pour attacher le profileur à une application web ASP.NET pour collecter des données concurrentielles en utilisant la ligne de commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d720779019ab4106fa6c4b727e9994f168a2d8f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179283"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Comment : attacher le profileur à une application Web ASP.NET pour collecter des données de concurrence en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique explique comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour attacher le profileur à une application ASP.NET et pour collecter des données de concurrence de processus et de threads.  

 Les outils en ligne de commande des outils de profilage se trouvent dans le sous-répertoire \Team Tools\Performance Tools du répertoire d’installation Visual Studio. Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser le profileur dans une fenêtre d’invite de commandes, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’**invite de commandes**, ou l’ajouter à la commande. Pour plus d’informations, consultez [Spécification du chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Pour collecter des données concurrentielles, attachez le profileur au processus de travail ASP.NET qui héberge votre site web. Lorsque le profileur est attaché à l’application, vous pouvez suspendre et reprendre la collecte de données. Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit plus être attaché à l’application et doit être arrêté explicitement. Dans la plupart des cas, vous devez supprimer les variables d’environnement de profilage à la fin d’une session.  

## <a name="attaching-the-profiler"></a>Attachement du profileur  

#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>Pour attacher le profileur à une application ASP.NET  

1. Démarrez le profileur en tapant la commande suivante :  

    [VSPerfCmd](../profiling/vsperfcmd.md) **/Start : concurrence/output :** `OutputFile` [ `Options` ]  

   - L’option [/start](../profiling/start.md) initialise le profileur pour collecter des données de conflit de ressources.  

   - L’option [/Output](../profiling/output.md)**:** `OutputFile` est requise avec **/Start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).  

     Vous pouvez utiliser l’une des options du tableau suivant avec l’option **/start**.  

   |                               Option                               |                                                                     Description                                                                      |
   |--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain\` ]`UserName` |                           Spécifie les noms de domaine et d’utilisateur facultatifs du compte qui doit obtenir l’accès au profileur.                           |
   |           [/CrossSession](../profiling/crosssession.md)            |                                               Active le profilage des processus dans d’autres sessions ouvertes.                                                |
   |  [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath`  |                                      Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage.                                       |
   |       [/AutoMark](../profiling/automark.md) **:**`Interval`       | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est 500. |
   |     [/Events](../profiling/events-vsperfcmd.md) **:**`Config`     |       Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl).       |

2. Démarrez l’application ASP.NET de manière classique.  

3. Attachez le profileur au processus de travail ASP.net en tapant la commande suivante :**VSPerfCmd/Attach :** `PID` [**/TargetCLR :** `Version` ]  

   - `PID` spécifie l’ID ou le nom du processus de travail ASP.NET. Vous pouvez afficher les ID de processus de tous les processus en cours d’exécution dans le gestionnaire des tâches de Windows.  

   - [/TargetCLR](../profiling/targetclr.md) **:** `Version` spécifie la version du Common Language Runtime (CLR) à profiler lorsque plusieurs versions du runtime sont chargées dans une application. Ce paramètre est optionnel.  

## <a name="controlling-data-collection"></a>Contrôle de la collection de données  
 Pendant l’exécution de l’application, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier à l’aide des options de VSPerfCmd.exe. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.  

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données  

- Les paires d’options VSPerfCmd du tableau suivant permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  

    |Option|Description|  
    |------------|-----------------|  
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|  
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [ProcessOff](../profiling/processon-and-processoff.md) **:**  `PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|  
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach** commence à collecter des données pour le processus spécifié par l’ID de processus (`PID`) ou le nom de processus (*ProcName*). **/detach** arrête la collecte des données pour le processus spécifié ou pour tous les processus, si aucun processus n’est spécifié.|  

## <a name="ending-the-profiling-session"></a>Fin d’une session de profilage  
 Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit pas être en train de collecter des données. Vous pouvez arrêter la collecte des données d’une application profilée avec la méthode d’accès concurrentiel en redémarrant le processus de travail ASP.NET ou en appelant l’option **VSPerfCmd /detach**. Vous devez alors appeler l’option **VSPerfCmd /shutdown** pour désactiver le profileur et fermer le fichier de données de profilage. La commande **VSPerfClrEnv /globaloff** efface les variables d’environnement de profilage. Toutefois, la configuration du système n’est pas réinitialisée tant que l’ordinateur n’a pas été redémarré.  

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage  

1. Détachez le profileur de l’application cible en fermant l’application ou en tapant la commande suivante à l’invite de commandes :  

     **VSPerfCmd /detach**  

2. Fermez le profileur en tapant ce qui suit à l’invite de commandes :  

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Voir aussi  
 [Profilage d’applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de site Web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
