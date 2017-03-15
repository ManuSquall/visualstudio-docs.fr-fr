---
title: "Comment&#160;: attacher le profileur &#224; une application Web ASP.NET pour collecter des statistiques d&#39;applications en utilisant la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: attacher le profileur &#224; une application Web ASP.NET pour collecter des statistiques d&#39;applications en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique explique comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à une application Web ASP.NET et collecter des statistiques de performance à l'aide de la méthode d'échantillonnage.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans Windows 8 et Windows Server 2012 nécessitaient d'importantes modifications de la manière dont le profileur Visual Studio collecte des données sur ces plateformes.  Les applications Windows Store requièrent également de nouvelles techniques de collecte.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  L'ajout de données d'interaction entre les couches à une exécution du profilage requiert des procédures spécifiques avec les outils de profilage de ligne de commande.  Consultez [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
>   
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] s  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre Invite de commandes ou l'ajouter à la commande elle\-même.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Pour collecter les données de performance d'une application Web ASP.NET, les variables d'environnement appropriées doivent être initialisées et l'ordinateur qui héberge l'application Web ASP.NET doit être redémarré pour configurer le serveur Web en vue du profilage.  
  
 Vous attachez alors le profileur au processus de travail ASP.NET qui héberge votre site Web.  Une fois le profileur attaché à l'application, vous pouvez suspendre la collecte de données et la reprendre.  
  
 Pour terminer une session de profilage, le profileur doit être détaché de l'application profilée et le profileur doit être arrêté explicitement.  Dans la plupart des cas, nous vous recommandons de désactiver les variables d'environnement de profilage à la fin d'une session.  
  
## Démarrage du profileur et attachement à une application Web ASP.NET  
  
#### Pour attacher le profileur à une application Web ASP.NET  
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Initialisez les variables d'environnement de profilage.  Type :  
  
     **VSPerfClrEnv \/globalsampleon** \[**\/samplelineoff**\]  
  
    -   **\/globalsampleon** active l'échantillonnage.  
  
    -   **\/samplelineoff** désactive l'assignation des données collectées à des lignes de code source spécifiques.  Lorsque cette option est spécifiée, les données sont assignées uniquement aux fonctions.  
  
3.  Redémarrez l'ordinateur.  
  
4.  Démarrez le profileur.  Tapez :**VSPerfCmd** [\/start](../profiling/start.md)**:sample** [\/output](../profiling/output.md)**:**`OutputFile`\[`Options`\]  
  
    -   L'option **\/start:sample** initialise le profileur.  
  
    -   L'option **\/output:**`OutputFile` est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser n'importe laquelle des options suivantes avec l'option **\/start:sample**.  
  
    > [!NOTE]
    >  Les options **\/user** et **\/crosssession** sont généralement requises pour les applications ASP.NET.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Spécifie le domaine et le nom d'utilisateur du compte qui possède le processus de travail ASP.NET.  Cette option est requise si le processus s'exécute en tant qu'utilisateur autre que l'utilisateur connecté.  Le propriétaire du processus est répertorié dans la colonne Nom d'utilisateur sous l'onglet Processus du Gestionnaire des tâches de Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Active le profilage de processus dans d'autres ouvertures de session.  Cette option est requise si l'application ASP.NET s'exécute dans une session différente.  L'identificateur de session est répertorié dans la colonne Identificateur de session sous l'onglet Processus du Gestionnaire des tâches de Windows.  **\/CS** peut être spécifié en tant qu'abréviation de **\/crosssession**.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est de 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie un événement ETW \(Event Tracing for Windows\) à collecter au cours du profilage.  Les événements ETW sont collectés dans un fichier séparé \(.etl\).|  
  
5.  Démarrez l'application Web ASP.NET de la manière classique.  
  
6.  Attachez le profileur au processus de travail ASP.NET.  Tapez :**VSPerfCmd** [\/attach](../profiling/attach.md)**:**{`PID` &#124;`ProcName`} \[`Sample Event`\] \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   `PID` spécifie l'ID du processus de travail ASP.NET ; `ProcName` spécifie le nom du processus de travail.  Vous pouvez afficher les ID et les noms de processus de tous les processus en cours d'exécution dans le Gestionnaire des tâches de Windows.  
  
    -   Par défaut, les données de performance sont échantillonnées après 10 millions de cycles d'horloge ininterrompus.  Cela correspond à environ 100 fois par seconde sur un processeur cadencé à 1 GHz.  Vous pouvez spécifier l'une des options **VSPerfCmd** suivantes pour modifier l'intervalle de cycle d'horloge ou pour spécifier un événement d'échantillonnage différent.  
  
    |Événement d'échantillonnage|Description|  
    |---------------------------------|-----------------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|Remplace l'intervalle d'échantillonnage par le nombre de cycles d'horloge ininterrompus spécifié par `Interval`.|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|Change l'événement d'échantillonnage en erreurs de page.  Si `Interval` est spécifié, définit le nombre d'erreurs de page entre les exemples.  La valeur par défaut est 10.|  
    |[\/sys](../profiling/sys-vsperfcmd.md)\[`:``Interval`\]|Change l'événement d'échantillonnage en appels système du processus au noyau du système d'exploitation \(syscalls\).  Si `Interval` est spécifié, définit le nombre d'appels entre les exemples.  La valeur par défaut est 10.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Remplace l'événement et l'intervalle d'échantillonnage par le compteur de performance de processeur et l'intervalle spécifiés dans `Config`.|  
    |[\/targetclr](../profiling/targetclr.md) **:** `Version`|Spécifie la version du Common Language Runtime \(CLR\) à profiler lorsque plusieurs versions du runtime sont chargées dans une application.|  
  
    -   **targetclr:** `Version` spécifie la version du Common Language Runtime \(CLR\) à profiler lorsque plusieurs versions du runtime sont chargées dans une application.  Optionnel.  
  
## Contrôle de la collecte de données  
 Lorsque l'application s'exécute, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l'écriture de données dans le fichier à l'aide des options **VSPerfCmd.exe**.  Le contrôle de la collecte de données vous permet de collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
#### Pour démarrer et arrêter la collecte de données  
  
-   Les paires suivantes d'options **VSPerfCmd** démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Démarre \(**\/globalon**\) ou arrête \(**\/globaloff**\) la collecte de données pour tous les processus.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` **\/processoff:**`PID`|Démarre \(**\/processon**\) ou arrête \(**\/processoff**\) la collecte de données pour le processus spécifié par `PID` \(l'ID de processus\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** commence à collecter des données pour le processus spécifié par le `PID` \(ID de processus\) ou le nom de processus \(ProcName\).  **\/detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus n'est spécifié.|  
  
## Fin de la session de profilage  
 Pour terminer une session de profilage, fermez l'application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], puis utilisez la commande des services IIS \(Internet Information Services\) **IISReset** pour fermer le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Appelez l'option **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) pour arrêter le profileur et fermer le fichier de données de profilage.  
  
 La commande **VSPerfClrEnv \/globaloff** désactive les variables d'environnement de profilage.  Vous devez redémarrer l'ordinateur pour que les nouveaux paramètres d'environnement soient appliqués.  
  
 La commande **VSPerfClrEnv \/globaloff** désactive les variables d'environnement de profilage, mais la configuration du système n'est réinitialisée qu'au redémarrage de l'ordinateur.  
  
#### Pour terminer une session de profilage  
  
1.  Effectuez l'une des opérations suivantes pour détacher le profileur de l'application cible :  
  
    -   Tapez **VSPerfCmd \/detach**  
  
         ou  
  
    -   Fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Arrêtez le profileur.  Tapez :**VSPerfCmd** [\/shutdown](../profiling/shutdown.md)  
  
3.  \(Facultatif\) Désactivez les variables d'environnement de profilage.  Type :  
  
     **VSPerfCmd \/globaloff**  
  
4.  Redémarrez l'ordinateur.  
  
## Voir aussi  
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Vues de données de la méthode d'échantillonnage](../profiling/profiler-sampling-method-data-views.md)