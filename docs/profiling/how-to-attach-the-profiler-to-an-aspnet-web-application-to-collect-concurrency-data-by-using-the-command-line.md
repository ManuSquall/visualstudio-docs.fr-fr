---
title: "Comment&#160;: attacher le profileur &#224; une application Web ASP.NET pour collecter des donn&#233;es de concurrence en utilisant la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: attacher le profileur &#224; une application Web ASP.NET pour collecter des donn&#233;es de concurrence en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à une application ASP.NET et collecter des données de concurrence de processus et de threads.  
  
 Les outils de ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de Visual Studio  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser le profileur à une invite de commandes, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre **Invite de commandes** ou l'ajouter à la commande elle\-même.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Pour collecter des données d'accès concurrentiel, vous attachez le profileur au processus de travail ASP .NET qui héberge votre site Web.  Lorsque le profileur est attaché à l'application, vous pouvez suspendre la collecte de données et la reprendre.  Pour terminer une session de profilage, le profileur ne doit plus être attaché à l'application et le profileur doit être arrêté explicitement.  Dans la plupart des cas, nous vous recommandons de désactiver les variables d'environnement de profilage à la fin d'une session.  
  
## Attachement du profileur  
  
#### Pour attacher le profileur à une application ASP.NET  
  
1.  Démarrez le profileur en tapant la commande suivante :  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency \/output:**`OutputFile` \[`Options`\]  
  
    -   L'option [\/start](../profiling/start.md) initialise le profileur afin de collecter des données de conflit de ressources.  
  
    -   L'option [\/output](../profiling/output.md)**:**`OutputFile`  est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser toute option figurant dans le tableau suivant avec l'option **\/start** .  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain\`\]`UserName`|Spécifie le domaine et le nom d'utilisateur facultatifs du compte qui se verra accorder l'accès au profileur.|  
    |[\/crosssession](../profiling/crosssession.md)|Active le profilage de processus dans d'autres ouvertures de session.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est 500.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie un événement ETW \(Event Tracing for Windows\) à collecter au cours du profilage.  Les événements ETW sont collectés dans un fichier séparé \(.etl\).|  
  
2.  Démarrez l'application ASP.NET de la manière classique.  
  
3.  Attachez le profileur au processus de travail ASP.NET en tapant la commande suivante :**VSPerfCmd \/attach:**`PID` \[**\/targetclr:**`Version`\]  
  
    -   `PID` spécifie l'ID ou le nom du processus de travail ASP.NET.  Vous pouvez afficher les ID de processus de tous les processus en cours d'exécution dans le Gestionnaire des tâches de Windows.  
  
    -   [\/targetclr](../profiling/targetclr.md) **:** `Version` spécifie la version du Common Language Runtime \(CLR\) à profiler lorsque plusieurs versions du runtime sont chargées dans une application.  Ce paramètre est optionnel.  
  
## Contrôle de la collecte de données  
 Lorsque l'application s'exécute, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l'écriture de données dans le fichier à l'aide des options VSPerfCmd.exe.  En contrôlant la collecte de données, vous pouvez collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
#### Pour démarrer et arrêter la collecte de données  
  
-   Les paires d'options VSPerfCmd dans la table suivante démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Démarre \(**\/globalon**\) ou arrête \(**\/globaloff**\) la collecte de données pour tous les processus.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [processoff](../profiling/processon-and-processoff.md) **:** `PID`|Démarre \(**\/processon**\) ou arrête \(**\/processoff**\) la collecte de données pour le processus spécifié par l'ID de processus \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** commence à collecter les données pour le processus spécifié par l'ID de processus \(`PID`\) ou le nom de processus \(*ProcName*\).  **\/detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus n'est spécifié.|  
  
## Fin de la session de profilage  
 Pour terminer une session de profilage, le profileur ne doit pas collecter des données.  Vous pouvez cesser de collecter des données d'une application profilée avec la méthode de concurrence en redémarrant le processus de travail ASP.NET ou en appelant l'option **VSPerfCmd \/detach**.  Vous appelez alors l'option **VSPerfCmd \/shutdown** pour arrêter le profileur et fermer le fichier de données de profilage.  La commande **VSPerfClrEnv \/globaloff** désactive les variables d'environnement de profilage, mais la configuration du système n'est réinitialisée qu'au redémarrage de l'ordinateur.  
  
#### Pour terminer une session de profilage  
  
1.  Détachez le profileur de l'application cible en le fermant ou en tapant la commande suivante à une invite de commandes :  
  
     **VSPerfCmd \/detach**  
  
2.  Arrêtez le profileur en tapant la commande suivante à une invite de commandes :  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## Voir aussi  
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de site Web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)