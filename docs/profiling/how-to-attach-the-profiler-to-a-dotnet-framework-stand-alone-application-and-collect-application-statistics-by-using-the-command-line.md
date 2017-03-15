---
title: "Comment&#160;: attacher le profileur &#224; une application .NET Framework autonome et collecter des statistiques d&#39;applications en utilisant la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: attacher le profileur &#224; une application .NET Framework autonome et collecter des statistiques d&#39;applications en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique explique comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à une application \(cliente\) autonome .NET Framework en cours d'exécution et collecter des statistiques de performance à l'aide de la méthode d'échantillonnage.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans Windows 8 et Windows Server 2012 nécessitaient d'importantes modifications de la manière dont le profileur Visual Studio collecte des données sur ces plateformes.  Les applications Windows Store requièrent également de nouvelles techniques de collecte.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] s  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre Invite de commandes ou l'ajouter à la commande elle\-même.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  L'ajout de données d'interaction entre les couches à une exécution du profilage requiert des procédures spécifiques avec les outils de profilage de ligne de commande.  Consultez [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Pour collecter les données de performance d'une application .NET Framework, les variables d'environnement appropriées doivent être initialisées avant le démarrage de l'application cible.  Une fois le profileur attaché à l'application, vous pouvez suspendre la collecte de données et la reprendre.  
  
 Pour terminer une session de profilage, le profileur ne doit plus être attaché à l'application et il doit être arrêté explicitement.  Dans la plupart des cas, nous vous recommandons de désactiver les variables d'environnement de profilage à la fin d'une session de profilage.  
  
## Attachement du profileur  
  
#### Pour attacher le profileur à une application .NET Framework en cours d'exécution  
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Initialisez les variables d'environnement de profilage.  Type :  
  
     **VSPerfClrEnv \/sampleon** \[**\/samplelineoff**\]  
  
    -   L'option **\/samplelineoff** désactive la collection de données de numéros de ligne du code source.  
  
3.  Démarrez le profileur.  Type :  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   L'option [\/start](../profiling/start.md)**:sample** initialise le profileur.  
  
    -   L'option [\/output](../profiling/output.md)**:**`OutputFile` est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser n'importe laquelle des options suivantes avec l'option **\/start:sample**.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Spécifie le domaine et le nom d'utilisateur facultatifs du compte qui possède le processus profilé.  Cette option est obligatoire uniquement si l'application profilée a été démarrée avec un utilisateur autre que celui qui a ouvert la session.|  
    |[\/crosssession](../profiling/crosssession.md)|Active le profilage de processus dans d'autres ouvertures de session.  **\/CS** peut être spécifié en tant qu'abréviation de **\/crosssession**.  Cette option est requise si l'application s'exécute dans une session différente.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est de 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie un événement ETW \(Event Tracing for Windows\) à collecter au cours du profilage.  Les événements ETW sont collectés dans un fichier séparé \(.etl\).|  
  
4.  Si nécessaire, démarrez l'application cible de la manière habituelle.  
  
5.  Attachez le profileur à l'application cible.  Type :  
  
     **VSPerfCmd \/attach:**{`PID`&#124;`ProcessName`} \[`Sample Event`\] \[**\/targetclr:**`Version`\]  
  
    -   `PID` spécifie l'ID de processus de l'application cible.  `ProcessName` spécifie le nom du processus.  Notez que si vous spécifiez `ProcessName` et que plusieurs processus du même nom sont en cours d'exécution, les résultats sont imprévisibles.  Vous pouvez afficher les ID de processus de tous les processus en cours d'exécution dans le Gestionnaire des tâches de Windows.  
  
    -   [\/targetclr](../profiling/targetclr.md) **:** `Version` spécifie la version du Common Language Runtime \(CLR\) à profiler lorsque plusieurs versions du runtime sont chargées dans une application.  Optionnel.  
  
    -   Par défaut, les données de performance sont échantillonnées après 10 millions de cycles d'horloge ininterrompus.  Cela correspond approximativement à une fois toutes les 10 secondes sur un processeur cadencé à 1 GHz.  Vous pouvez spécifier l'une des options suivantes pour modifier l'intervalle de cycle d'horloge ou pour spécifier un événement d'échantillonnage différent.[\/targetclr](../profiling/targetclr.md)**:**`Version` spécifie la version du Common Language Runtime \(CLR\) à profiler lorsque plusieurs versions du runtime sont chargées dans une application.  Optionnel.  
  
    |||  
    |-|-|  
    |Événement d'échantillonnage|Description|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|Remplace l'intervalle d'échantillonnage par le nombre de cycles d'horloge ininterrompus spécifié par `Interval`.|  
    |[\/pf](../profiling/pf.md) \[**:**`Interval`\]|Change l'événement d'échantillonnage en erreurs de page.  Si `Interval` est spécifié, définit le nombre d'erreurs de page entre les exemples.  La valeur par défaut est 10.|  
    |[\/sys](../profiling/sys-vsperfcmd.md) \[**:**`Interval`\]|Change l'événement d'échantillonnage en appels système du processus au noyau du système d'exploitation \(syscalls\).  Si `Interval` est spécifié, définit le nombre d'appels entre les exemples.  La valeur par défaut est 10.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Remplace l'événement et l'intervalle d'échantillonnage par le compteur de performance de processeur et l'intervalle spécifiés dans `Config`.|  
  
## Contrôle de la collecte de données  
 Lorsque l'application cible s'exécute, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l'écriture de données dans le fichier de données du profileur à l'aide des options **VSPerfCmd.exe**.  Le contrôle de la collecte de données vous permet de collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
#### Pour démarrer et arrêter la collecte de données  
  
-   Les paires suivantes d'options démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Démarre \(**\/globalon**\) ou arrête \(**\/globaloff**\) la collecte de données pour tous les processus.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Démarre \(**\/processon**\) ou arrête \(**\/processoff**\) la collecte de données pour le processus spécifié par `PID` \(l'ID de processus\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** commence à collecter des données pour le processus spécifié par l'ID de processus \(`PID`\) ou le nom de processus \(ProcName\).  **\/detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus n'est spécifié.|  
  
## Fin de la session de profilage  
 Pour terminer une session de profilage, le profileur doit être détaché de tous les processus profilés et arrêté explicitement.  Vous pouvez détacher le profileur d'une application qui a été profilée via la méthode d'échantillonnage en fermant l'application ou en appelant l'option **VSPerfCmd \/detach**.  Vous appelez alors l'option **VSPerfCmd \/shutdown** pour arrêter le profileur et fermer le fichier de données de profilage.  La commande **VSPerfClrEnv \/off** désactive les variables d'environnement de profilage.  
  
#### Pour terminer une session de profilage  
  
1.  Effectuez l'une des étapes suivantes pour détacher le profileur de l'application cible :  
  
    -   Tapez **VSPerfCmd \/detach**  
  
         ou  
  
    -   Fermez l'application cible.  
  
2.  Arrêtez le profileur.  Type :  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
3.  \(Facultatif\) Désactivez les variables d'environnement de profilage.  Type :  
  
     **VSPerfClrEnv \/off**  
  
## Voir aussi  
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Vues de données de la méthode d'échantillonnage](../profiling/profiler-sampling-method-data-views.md)