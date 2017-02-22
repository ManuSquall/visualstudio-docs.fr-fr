---
title: "Comment&#160;: lancer une application .NET Framework autonome avec le profileur pour collecter des donn&#233;es de concurrence en utilisant la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: lancer une application .NET Framework autonome avec le profileur pour collecter des donn&#233;es de concurrence en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour démarrer une application autonome \(cliente\) du .NET Framework et collecter des données de concurrence de processus et de threads.  
  
> [!NOTE]
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] s  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre Invite de commandes ou l'ajouter à la commande elle\-même.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Lorsque le profileur est attaché à l'application, vous pouvez suspendre la collecte de données et la reprendre.  Pour terminer une session de profilage, le profileur ne doit plus être attaché à l'application et le profileur doit être arrêté explicitement.  
  
## Démarrage de l'application avec le profileur  
 Pour lancer une application cible .NET Framework avec le profileur, vous utilisez VSPerfClrEnv.exe pour définir les variables de profilage .NET Framework.  Vous utilisez alors les options VSPerfCmd **\/start** et **\/launch** pour initialiser le profileur et démarrer l'application.  Vous pouvez spécifier **\/start** et **\/launch** et leurs options respectives sur une ligne de commande unique.  Vous pouvez également ajouter l'option **\/globaloff** à la ligne de commande pour suspendre la collecte de données lorsque l'application cible démarre.  Vous utilisez alors **\/globalon** sur une ligne de commande séparée pour commencer à collecter des données.  
  
#### Pour démarrer une application avec le profileur  
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Démarrez le profileur.  Type :  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency**\[**,**{**ResourceOnly**&#124;**ThreadOnly**}\] **\/output:**`OutputFile` \[`Options`\]  
  
    -   L'option [\/start](../profiling/start.md) initialise le profileur.  
  
        |||  
        |-|-|  
        |**\/start:concurrency**|Active la collection des données de conflit de ressources et d'exécution de thread.|  
        |**\/start:concurrency,resourceonly**|Active la collection des données de conflit de ressources uniquement.|  
        |**\/start:concurrency,threadonly**|Active la collection des données d'exécution de thread uniquement.|  
  
    -   L'option [\/output](../profiling/output.md)**:**`OutputFile` est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser n'importe laquelle des options suivantes avec l'option **\/start:concurrency** .  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/utilisateur](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|Spécifie le domaine et le nom d'utilisateur facultatifs du compte qui se verra accorder l'accès au profileur.|  
    |[\/crosssession](../profiling/crosssession.md)|Active le profilage de processus dans d'autres ouvertures de session.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est de 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie un événement ETW \(Event Tracing for Windows\) à collecter au cours du profilage.  Les événements ETW sont collectés dans un fichier séparé \(.etl\).|  
  
3.  Démarrez l'application cible.  Type :  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `AppName` \[`Options`\] \[`Sample Event`\]  
  
     Vous pouvez utiliser n'importe laquelle des options suivantes avec l'option **\/launch**.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|Spécifie une chaîne qui contient les arguments de ligne de commande à passer à l'application cible.|  
    |[\/console](../profiling/console.md)|Démarre l'application en ligne de commande cible dans une fenêtre séparée.|  
    |[\/targetclr](../profiling/targetclr.md) **:** `Version`|Spécifie la version du Common Language Runtime \(CLR\) à profiler lorsque plusieurs versions du runtime sont chargées dans une application.|  
  
## Contrôle de la collecte de données  
 Lorsque l'application cible s'exécute, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l'écriture de données dans le fichier à l'aide des options VSPerfCmd.exe.  Le contrôle de la collecte de données vous permet de collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
#### Pour démarrer et arrêter la collecte de données  
  
1.  Les paires d'options VSPerfCmd.exe suivantes démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Démarre \(**\/globalon**\) ou arrête \(**\/globaloff**\) la collecte de données pour tous les processus.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Démarre \(**\/processon**\) ou arrête \(**\/processoff**\) la collecte de données pour le processus spécifié par l'ID de processus \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** commence à collecter des données pour le processus spécifié par l'ID de processus \(`PID`\) ou le nom de processus \(ProcName\).  **\/detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus n'est spécifié.|  
  
## Fin de la session de profilage  
 Pour terminer une session de profilage, le profileur ne doit pas collecter des données.  Vous pouvez cesser de collecter des données d'accès concurrentiel en fermant l'application profilée ou en appelant l'option **VSPerfCmd \/detach**.  Vous appelez alors l'option **VSPerfCmd \/shutdown** pour arrêter le profileur et fermer le fichier de données de profilage.  La commande **VSPerfClrEnv \/off** désactive les variables d'environnement de profilage.  
  
#### Pour terminer une session de profilage  
  
1.  Effectuez l'une des opérations suivantes pour détacher le profileur de l'application cible.  
  
    -   Fermez l'application cible.  
  
         ou  
  
    -   Tapez **VSPerfCmd \/detach**  
  
2.  Fermez le profileur  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## Voir aussi  
 [Collecte de données concurrentielles](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)