---
title: "Comment&#160;: attacher le profileur &#224; un service natif pour collecter des statistiques d&#39;applications en utilisant la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: attacher le profileur &#224; un service natif pour collecter des statistiques d&#39;applications en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique explique comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à un service natif et collecter des statistiques de performance à l'aide de la méthode d'échantillonnage.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans Windows 8 et Windows Server 2012 nécessitaient d'importantes modifications de la manière dont le profileur Visual Studio collecte des données sur ces plateformes.  Les applications Windows Store requièrent également de nouvelles techniques de collecte.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] s  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre d'invite de commandes ou l'ajouter à la commande elle\-même.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Lorsque le profileur est attaché au service, vous pouvez suspendre la collecte de données et la reprendre.  
  
 Pour terminer une session de profilage, le profileur doit être détaché du service et le profileur doit être arrêté explicitement.  
  
## Démarrage de l'application avec le profileur  
 Pour attacher le profileur à un service natif, utilisez les options **VSPerfCmd.exe** [\/start](../profiling/start.md) et [\/attach](../profiling/attach.md) pour initialiser le profileur et l'attacher à l'application cible.  Vous pouvez spécifier **\/start** et **\/attach** et leurs options respectives sur une ligne de commande unique.  Vous pouvez également ajouter l'option [\/globaloff](../profiling/globalon-and-globaloff.md) pour suspendre la collecte de données au démarrage de l'application cible.  Vous pouvez ensuite utiliser [\/globalon](../profiling/globalon-and-globaloff.md) pour commencer à collecter les données.  
  
#### Pour attacher le profileur à un service natif  
  
1.  Si nécessaire, démarrez le service.  
  
2.  Ouvrez une fenêtre d'invite de commandes.  
  
3.  Démarrez le profileur.  Type :  
  
     **VSPerfCmd \/start:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   L'option **\/start:sample** initialise le profileur.  
  
    -   L'option **\/output:**`OutputFile` est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser n'importe laquelle des options suivantes avec l'option **\/start:sample**.  
  
    > [!NOTE]
    >  Les options **\/user** et **\/crosssession** sont généralement requises pour les services.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Spécifie le domaine et le nom d'utilisateur du compte qui possède le processus profilé.  Cette option est uniquement requise si le processus s'exécute en tant qu'un utilisateur autre que l'utilisateur connecté.  Le propriétaire du processus est répertorié dans la colonne Nom d'utilisateur sous l'onglet Processus du Gestionnaire des tâches de Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Active le profilage de processus dans d'autres sessions.  Cette option est requise si l'application s'exécute dans une session différente.  L'identificateur de session est répertorié dans la colonne Identificateur de session sous l'onglet Processus du Gestionnaire des tâches de Windows.  **\/CS** peut être spécifié en tant qu'abréviation de **\/crosssession**.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est de 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie un événement ETW \(Event Tracing for Windows\) à collecter au cours du profilage.  Les événements ETW sont collectés dans un fichier séparé \(.etl\).|  
  
4.  Attachez le profileur au service.  Type :  
  
     **VSPerfCmd \/attach:** `PID` \[`Sample Event`\]  
  
     `PID` spécifie l'ID de processus de l'application cible.  Vous pouvez afficher les ID de processus de tous les processus en cours d'exécution dans le Gestionnaire des tâches de Windows.  
  
     Par défaut, les données de performance sont échantillonnées après 10 millions de cycles d'horloge ininterrompus.  Cela correspond approximativement à une fois toutes les 10 secondes sur un processeur cadencé à 1 GHz.  Vous pouvez spécifier l'une des options suivantes pour modifier l'intervalle de cycle d'horloge ou pour spécifier un événement d'échantillonnage différent.  
  
    |Événement d'échantillonnage|Description|  
    |---------------------------------|-----------------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|Change l'intervalle d'échantillonnage en nombre de cycles d'horloge ininterrompus spécifié par `Interval`.|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|Change l'événement d'échantillonnage en erreurs de page.  Si `Interval` est spécifié, définit le nombre d'erreurs de page entre les exemples.  La valeur par défaut est 10.|  
    |[\/sys](../profiling/sys-vsperfcmd.md) \[**:**`Interval`\]|Change l'événement d'échantillonnage en appels système du processus au noyau du système d'exploitation \(syscalls\).  Si `Interval` est spécifié, définit le nombre d'appels entre les exemples.  La valeur par défaut est 10.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Remplace l'événement et l'intervalle d'échantillonnage par le compteur de performance de processeur et l'intervalle spécifiés dans `Config`.|  
  
## Contrôle de la collecte de données  
 Lors de l'exécution de l'application cible, vous pouvez utiliser les options **VSPerfCmd.exe** pour démarrer et arrêter l'écriture de données dans le fichier de données du profileur.  Le contrôle de la collecte de données vous permet de collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
#### Pour démarrer et arrêter la collecte de données  
  
-   Les paires suivantes d'options **VSPerfCmd** démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Démarre \(**\/globalon**\) ou arrête \(**\/globaloff**\) la collecte de données pour tous les processus.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Démarre \(**\/processon**\) ou arrête \(**\/processoff**\) la collecte de données pour le processus spécifié par l'ID de processus \(`PID`\).|  
    |**\/attach:** {`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[:{`PID`&#124;`ProcName`}\]|**\/attach** commence à collecter des données pour le processus spécifié par l'ID de processus ou le nom de processus.  **\/detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus n'est spécifié.|  
  
## Fin de la session de profilage  
 Pour terminer une session de profilage, le profileur doit être détaché du service puis arrêté explicitement.  Vous pouvez détacher le service natif profilé avec la méthode d'échantillonnage en arrêtant le service ou en appelant l'option **VSPerfCmd \/detach**.  Appelez ensuite l'option **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) pour arrêter le profileur et fermer le fichier de données de profilage.  
  
#### Pour terminer une session de profilage  
  
1.  Effectuez l'une des opérations suivantes pour détacher le profileur de l'application cible :  
  
    -   Arrêtez le service.  
  
         ou  
  
    -   Tapez **VSPerfCmd \/detach**  
  
2.  Arrêtez le profileur.  Type :  
  
     **VSPerfCmd \/shutdown**  
  
## Voir aussi  
 [Profilage de services](../profiling/command-line-profiling-of-services.md)   
 [Vues de données de la méthode d'échantillonnage](../profiling/profiler-sampling-method-data-views.md)