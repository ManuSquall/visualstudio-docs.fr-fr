---
title: "Comment&#160;: lancer une application autonome avec le profileur et collecter des statistiques d&#39;applications en utilisant la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: lancer une application autonome avec le profileur et collecter des statistiques d&#39;applications en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour démarrer une application autonome \(cliente\) et collecter des statistiques de performance à l'aide de la méthode d'échantillonnage.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans Windows 8 et Windows Server 2012 nécessitaient d'importantes modifications de la manière dont le profileur Visual Studio collecte des données sur ces plateformes.  Les applications Windows Store requièrent également de nouvelles techniques de collecte.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  L'ajout de données d'interaction entre les couches à une exécution du profilage requiert des procédures spécifiques avec les outils de profilage de ligne de commande.  Consultez [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin d'accès de la variable d'environnement PATH de la fenêtre Invite de commandes ou l'ajouter à la commande elle\-même.  Vous pouvez exécuter les outils de profilage sur un ordinateur où Visual Studio est installé à partir d'une fenêtre de commande Visual Studio.  
  
1.  Si vous exécutez les outils de profilage sur un ordinateur où Visual Studio est installé une fenêtre de commande Visual Studio définit les chemins d'accès correct.  Dans le menu **Outils**, choisissez **VS invite de commandes**  
  
> [!NOTE]
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de Visual Studio  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin d'accès de la variable d'environnement PATH de la fenêtre Invite de commandes ou l'ajouter à la commande elle\-même.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Démarrage de l'application avec le profileur  
 Pour démarrer une application cible avec le profileur, utilisez les options **\/start** et **\/launch** pour initialiser le profileur et démarrer l'application.  Vous pouvez spécifier **\/start** et **\/launch** et leurs options respectives sur une ligne de commande unique.  
  
 Vous pouvez également ajouter l'option **\/globaloff** pour suspendre la collecte de données au démarrage de l'application cible.  Vous utilisez alors **\/globalon** pour commencer à collecter des données.  
  
#### Pour démarrer l'application à l'aide du profileur  
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Démarrez le profileur.  Type :  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   L'option [\/start](../profiling/start.md)**:sample** initialise le profileur.  
  
    -   L'option [\/output](../profiling/output.md)**:**`OutputFile` est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser n'importe laquelle des options suivantes avec l'option **\/start:sample**.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est de 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie un événement ETW \(Event Tracing for Windows\) à collecter au cours du profilage.  Les événements ETW sont collectés dans un fichier séparé \(.etl\).|  
  
3.  Démarrez l'application cible.  Tapez :**VSPerfCmd \/launch:**`appName` \[`Options`\] \[`Sample Event`\]  
  
     Vous pouvez utiliser une ou plusieurs des options suivantes avec l'option **\/launch**.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|Spécifie une chaîne qui contient les arguments de ligne de commande à passer à l'application cible.|  
    |[\/console](../profiling/console.md)|Démarre l'application en ligne de commande cible dans une fenêtre séparée.|  
  
     Par défaut, les données de performance sont échantillonnées après 10 millions de cycles d'horloge ininterrompus.  Cela correspond approximativement à une fois toutes les 10 secondes sur un processeur cadencé à 1 GHz.  Vous pouvez spécifier l'une des options suivantes pour modifier l'intervalle de cycle d'horloge ou pour spécifier un événement d'échantillonnage différent.  
  
    |Événement d'échantillonnage|Description|  
    |---------------------------------|-----------------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|Remplace l'intervalle d'échantillonnage par le nombre de cycles d'horloge ininterrompus spécifié par `Interval`.|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|Change l'événement d'échantillonnage en erreurs de page.  Si `Interval` est spécifié, définit le nombre d'erreurs de page entre les exemples.  La valeur par défaut est 10.|  
    |[\/sys](../profiling/sys-vsperfcmd.md)\[**:**`Interval`\]|Change l'événement d'échantillonnage en appels système du processus au noyau du système d'exploitation \(syscalls\).  Si `Interval` est spécifié, définit le nombre d'appels entre les exemples.  La valeur par défaut est 10.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Remplace l'événement et l'intervalle d'échantillonnage par le compteur de performance de processeur et l'intervalle spécifiés dans `Config`.|  
  
## Contrôle de la collecte de données  
 Lorsque l'application cible s'exécute, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l'écriture de données dans le fichier de données du profileur à l'aide des options **VSPerfCmd.exe**.  Le contrôle de la collecte de données vous permet de collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
#### Pour démarrer et arrêter la collecte de données  
  
-   Les paires suivantes d'options démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Démarre \(**\/globalon**\) ou arrête \(**\/globaloff**\) la collecte de données pour tous les processus.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [\/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Démarre \(**\/processon**\) ou arrête \(**\/processoff**\) la collecte de données pour le processus spécifié par l'ID de processus \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** commence à collecter des données pour le processus spécifié par le `PID` \(ID de processus\) ou le nom de processus \(ProcName\).  **\/detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus n'est spécifié.|  
  
## Fin de la session de profilage  
 Pour terminer une session de profilage, le profileur doit être détaché de tout processus profilé et le profileur doit être arrêté explicitement.  Vous pouvez détacher le profileur d'une application qui a été profilée via la méthode d'échantillonnage en fermant l'application ou en appelant l'option **VSPerfCmd \/detach**.  Vous appelez alors l'option **VSPerfCmd \/shutdown** pour arrêter le profileur et fermer le fichier de données de profilage.  La commande **VSPerfClrEnv \/off** désactive les variables d'environnement de profilage.  
  
#### Pour terminer une session de profilage  
  
1.  Effectuez l'une des étapes suivantes pour détacher le profileur de l'application cible :  
  
    -   Fermez l'application cible.  
  
         ou  
  
    -   Tapez **VSPerfCmd \/detach**  
  
2.  Arrêtez le profileur.  Type :  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## Voir aussi  
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Vues de données de la méthode d'échantillonnage](../profiling/profiler-sampling-method-data-views.md)