---
title: "Comment&#160;: lancer une application native autonome avec le profileur pour collecter des donn&#233;es d&#39;acc&#232;s concurrentiel en utilisant la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: lancer une application native autonome avec le profileur pour collecter des donn&#233;es d&#39;acc&#232;s concurrentiel en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique explique comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour démarrer une application \(cliente\) autonome native et collecter des données d'accès concurrentiel de processus et de threads.  
  
 Une session de profilage comporte les opérations suivantes :  
  
-   démarrage de l'application avec le profileur ;  
  
-   contrôle de la collecte des données ;  
  
-   Fin de la session de profilage  
  
> [!NOTE]
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] s  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser le profileur à une invite de commandes, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre **Invite de commandes** ou l'ajouter à la commande elle\-même.  Pour plus d’informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Démarrage de l'application avec le profileur  
 Pour démarrer une application cible avec le profileur, utilisez les options [VSPerfCmd.exe](../profiling/vsperfcmd.md) **\/start** et **\/launch** pour initialiser le profileur et démarrer l'application.  Vous pouvez spécifier **\/start** et **\/launch** et leurs options respectives.  Vous pouvez également ajouter l'option **\/globaloff** pour suspendre la collecte de données au démarrage de l'application cible.  Vous utilisez alors **\/globalon** pour commencer à collecter des données.  
  
#### Pour démarrer une application avec le profileur  
  
1.  À l'invite de commandes, entrez la commande suivante :  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
     L'option [\/output](../profiling/output.md)**:**`OutputFile` est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser n'importe laquelle des options figurant dans le tableau suivant avec l'option **\/start:concurrency** .  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est 500.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie un événement ETW \(Event Tracing for Windows\) à collecter au cours du profilage.  Les événements ETW sont collectés dans un fichier séparé \(.etl\).|  
  
2.  Démarrez l'application cible en tapant ce qui suit :  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `AppName` \[`Options`\]  
  
     Vous pouvez utiliser l'une des options figurant dans le tableau suivant avec l'option **\/launch**.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|Spécifie une chaîne qui contient les arguments de ligne de commande à passer à l'application cible.|  
    |[\/console](../profiling/console.md)|Démarre l'application en ligne de commande cible dans une fenêtre séparée.|  
    |[\/targetclr](../profiling/targetclr.md) **:** `CLRVersion`|Spécifie la version du Common Language Runtime \(CLR\) à profiler si l'application charge plusieurs versions du CLR.|  
  
## Contrôle de la collecte de données  
 Lorsque l'application cible s'exécute, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l'écriture de données dans le fichier à l'aide des options VSPerfCmd.exe.  En contrôlant la collecte de données, vous pouvez collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
#### Pour démarrer et arrêter la collecte de données  
  
-   Les paires d'options dans la table suivante démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Démarre \(**\/globalon**\) ou arrête \(**\/globaloff**\) la collecte de données pour tous les processus.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Démarre \(**\/processon**\) ou arrête \(**\/processoff**\) la collecte de données pour le processus spécifié par l'ID de processus \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** commence à collecter des données pour le processus spécifié par l'ID de processus \(`PID`\) ou le nom de processus \(*ProcName*\).  **\/detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus n'est spécifié.|  
  
-   Vous pouvez également utiliser l'option **VSPerfCmd.exe** [\/mark](../profiling/mark.md) pour insérer une marque de profilage dans le fichier de données.  La commande **\/mark** ajoute un identificateur, un horodatage et une chaîne de texte facultative définie par l'utilisateur.  Les marques peuvent servir à filtrer les données dans les rapports et les vues de données du profileur.  
  
## Fin de la session de profilage  
 Pour terminer une session de profilage, le profileur ne doit pas collecter des données.  Vous pouvez cesser de collecter des données d'accès concurrentiel en fermant l'application profilée ou en appelant l'option **VSPerfCmd \/detach**.  Vous appelez alors l'option **VSPerfCmd \/shutdown** pour arrêter le profileur et fermer le fichier de données de profilage.  
  
#### Pour terminer une session de profilage  
  
1.  Détachez le profileur de l'application cible en le fermant ou en tapant la commande suivante à une invite de commandes :  
  
     **VSPerfCmd \/detach**  
  
2.  Arrêtez le profileur en tapant la commande suivante à une invite de commandes :  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)