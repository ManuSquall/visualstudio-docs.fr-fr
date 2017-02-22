---
title: "Comment&#160;: attacher le profileur &#224; un service natif pour collecter des donn&#233;es de concurrence en utilisant la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: attacher le profileur &#224; un service natif pour collecter des donn&#233;es de concurrence en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à un service natif \(C\/C\+\+\) et collecter des données de concurrence de processus et de threads à l'aide de la méthode d'échantillonnage.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans Windows 8 et Windows Server 2012 nécessitaient d'importantes modifications de la manière dont le profileur Visual Studio collecte des données sur ces plateformes.  Les applications Windows Store requièrent également de nouvelles techniques de collecte.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Les outils de ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de Visual Studio  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser le profileur à une invite de commandes, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre **Invite de commandes** ou à la commande elle\-même.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Lorsque le profileur est attaché au service, vous pouvez suspendre la collecte de données et la reprendre.  Pour terminer une session de profilage, le profileur ne doit plus être attaché au service et doit être explicitement arrêté.  
  
## Attachement du profileur  
 Pour attacher le profileur à un service natif, vous utilisez les options **VSPerfCmd \/start** et **\/attach** pour initialiser le profileur et l'attacher à l'application cible.  Vous pouvez spécifier **\/start** et **\/attach** et leurs options respectives sur une ligne de commande unique.  Vous pouvez également ajouter l'option **\/globaloff** pour suspendre la collecte de données au démarrage de l'application cible.  Vous utilisez alors **\/globalon** pour commencer à collecter des données.  
  
#### Pour attacher le profileur à un service natif  
  
1.  Si ce service ne s'exécute pas, démarrez\-le.  
  
2.  Démarrez le profileur en tapant ce qui suit à une invite de commandes :  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
    -   L'option [\/output](../profiling/output.md)**:**`OutputFile` est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser toute option figurant dans le tableau suivant avec l'option **\/start** .  
  
    > [!NOTE]
    >  La plupart des services requièrent les options **\/user** et **\/crosssession**.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain\`\]`UserName`|Spécifie le domaine et le nom d'utilisateur facultatifs du compte qui se verra accorder l'accès au profileur.|  
    |[\/crosssession](../profiling/crosssession.md)|Active le profilage de processus dans d'autres ouvertures de session.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est 500.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie un événement ETW \(Event Tracing for Windows\) à collecter au cours du profilage.  Les événements ETW sont collectés dans un fichier séparé \(.etl\).|  
  
3.  Attachez le profileur au service en tapant la commande suivante à une invite de commandes :  
  
     **VSPerfCmd \/attach:** `PID`  
  
     `PID` spécifie l'ID de processus ou le nom du processus de l'application cible.  Vous pouvez afficher les ID de processus de tous les processus en cours d'exécution dans le Gestionnaire des tâches de Windows.  
  
## Contrôle de la collecte de données  
 Lorsque l'application cible s'exécute, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l'écriture de données dans le fichier à l'aide des options VSPerfCmd.exe.  En contrôlant la collecte de données, vous pouvez collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
#### Pour démarrer et arrêter la collecte de données  
  
-   Les paires d'options dans la table suivante démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Démarre \(**\/globalon**\) ou arrête \(**\/globaloff**\) la collecte de données pour tous les processus.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Démarre \(**\/processon**\) ou arrête \(**\/processoff**\) la collecte de données pour le processus spécifié par l'ID de processus \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** commence à collecter les données pour le processus spécifié par l'ID de processus \(`PID`\) ou le nom de processus \(*ProcName*\).  **\/detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus n'est spécifié.|  
  
## Fin de la session de profilage  
 Pour terminer une session de profilage, le profileur ne doit pas collecter des données.  Vous pouvez cesser de collecter des données d'un service natif profilé avec la méthode de concurrence en arrêtant le service ou en appelant l'option **VSPerfCmd \/detach**.  Vous appelez alors l'option **VSPerfCmd \/shutdown** pour arrêter le profileur et fermer le fichier de données de profilage.  
  
#### Pour terminer une session de profilage  
  
1.  Détachez le profileur de l'application cible en arrêtant le service ou en tapant la commande suivante à une invite de commandes :  
  
     Tapez **VSPerfCmd \/detach**  
  
2.  Arrêtez le profileur en tapant la commande suivante à une invite de commandes :  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)