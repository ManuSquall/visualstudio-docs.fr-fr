---
title: "Comment&#160;: attacher le profileur &#224; une application Web ASP.NET pour collecter des donn&#233;es de m&#233;moire en utilisant la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: attacher le profileur &#224; une application Web ASP.NET pour collecter des donn&#233;es de m&#233;moire en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique explique comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à une application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] et collecter des données sur le nombre et la taille des allocations de mémoire .NET Framework.  Vous pouvez également collecter des données sur la durée de vie des objets mémoire .NET Framework.  
  
> [!NOTE]
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] s  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre Invite de commandes ou l'ajouter à la commande elle\-même.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Pour collecter les données de performance d'une application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], vous devez utiliser l'outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d'environnement appropriées sur l'ordinateur qui héberge l'application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Vous devez ensuite redémarrer l'ordinateur pour configurer le serveur Web pour le profilage.  
  
 Utilisez ensuite l'outil [VSPerfCmd.exe](../profiling/vsperfcmd.md) pour attacher le profileur au processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] qui héberge votre site Web.  Une fois le profileur attaché à l'application, vous pouvez suspendre la collecte de données et la reprendre.  
  
 Pour terminer une session de profilage, le profileur ne doit plus être attaché à l'application et il doit être arrêté explicitement.  Dans la plupart des cas, nous vous recommandons de désactiver les variables d'environnement de profilage à la fin d'une session.  
  
## Attachement du profileur  
  
#### Pour attacher le profileur à une application Web ASP.NET  
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Initialisez les variables d'environnement de profilage.  Type :  
  
     **VSPerfClrEnv** {**\/globalsamplegc** &#124; **\/globalsamplegclife**} \[**\/samplelineoff**\]  
  
    -   Les options **\/globalsamplegc** et **\/globalsamplegclife** spécifient le type de données de mémoire à collecter.  
  
         Spécifiez une seule des options suivantes.  
  
        |Option|Description|  
        |------------|-----------------|  
        |**\/globalsamplegc**|Active la collecte des données d'allocation de mémoire.|  
        |**\/globalsamplegclife**|Active la collecte des données d'allocation de mémoire et des données de durée de vie d'objets.|  
  
    -   L'option **\/samplelineoff** désactive l'assignation des données collectées à des lignes de code source spécifiques.  Si cette option est spécifiée, les données sont assignées au niveau de la fonction.  
  
3.  Redémarrez l'ordinateur pour définir la nouvelle configuration de l'environnement.  
  
4.  Ouvrez une fenêtre d'invite de commandes.  Si nécessaire, définissez la variable d'environnement de chemin d'accès du profileur.  
  
5.  Démarrez le profileur.  Type :  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   L'option **\/start:sample** initialise le profileur.  
  
    -   L'option **\/output:**`OutputFile` est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser n'importe laquelle des options suivantes avec l'option **\/start:sample**.  
  
    > [!NOTE]
    >  Les options **\/user** et **\/crosssession** sont généralement requises pour les applications ASP.NET.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Spécifie le domaine et le nom d'utilisateur du compte qui possède le processus de travail ASP.NET.  Cette option est requise si le processus s'exécute en tant qu'utilisateur autre que l'utilisateur connecté.  Le propriétaire du processus est répertorié dans la colonne Nom d'utilisateur sous l'onglet Processus du Gestionnaire des tâches de Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Active le profilage de processus dans d'autres ouvertures de session.  Cette option est requise si l'application ASP.NET s'exécute dans une session différente.  L'identificateur de session est répertorié dans la colonne Identificateur de session sous l'onglet Processus du Gestionnaire des tâches de Windows.  **\/CS** peut être spécifié en tant qu'abréviation de **\/crosssession**.|  
    |[\/waitstart](../profiling/waitstart.md) \[**:**`Interval`\]|Spécifie le nombre de secondes d'attente lors de l'initialisation du profileur avant qu'une erreur ne soit retournée.  Si `Interval` n'est pas spécifié, le profileur attend indéfiniment.  Par défaut, **\/start** est immédiatement retourné.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est de 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie un événement ETW \(Event Tracing for Windows\) à collecter au cours du profilage.  Les événements ETW sont collectés dans un fichier séparé \(.etl\).|  
  
6.  Démarrez l'application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de manière classique.  
  
7.  Attachez le profileur au processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Type :  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   L'ID de processus `(PID)` spécifie l'ID ou le nom du processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Vous pouvez afficher les ID de processus de tous les processus en cours d'exécution dans le Gestionnaire des tâches de Windows.  
  
    -   **\/targetclr:** `Version` spécifie la version du Common Language Runtime \(CLR\) à profiler lorsque plusieurs versions du runtime sont chargées dans une application.  
  
## Contrôle de la collecte de données  
 Pendant l'exécution de l'application, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l'écriture de données dans le fichier de données du profileur à l'aide des options **VSPerfCmd.exe**.  Le contrôle de la collecte de données vous permet de collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
#### Pour démarrer et arrêter la collecte de données  
  
-   Les paires suivantes d'options **VSPerfCmd** démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Démarre \(**\/globalon**\) ou arrête \(**\/globaloff**\) la collecte de données pour tous les processus.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Démarre \(**\/processon**\) ou arrête \(**\/processoff**\) la collecte de données pour le processus spécifié par le `PID`.|  
    |**\/attach:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;:`ProcName`}\]|**\/attach** commence à collecter des données pour le processus spécifié par l'ID de processus ou le nom de processus.  **\/detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus n'est spécifié.|  
  
## Fin de la session de profilage  
 Pour terminer une session de profilage, détachez le profileur de l'application Web.  Vous pouvez arrêter la collecte de données sur une application profilée avec la méthode d'échantillonnage en redémarrant le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ou en appelant l'option **VSPerfCmd \/detach**.  Appelez ensuite l'option **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) pour arrêter le profileur et fermer le fichier de données de profilage.  La commande **VSPerfClrEnv \/globaloff** désactive les variables d'environnement de profilage, mais la configuration du système n'est réinitialisée qu'au redémarrage de l'ordinateur.  
  
#### Pour terminer une session de profilage  
  
1.  Effectuez l'une des étapes suivantes pour détacher le profileur de l'application cible :  
  
    -   Tapez **VSPerfCmd** [\/detach](../profiling/detach.md)  
  
         ou  
  
    -   Fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Type :  
  
     **IISReset \/stop**  
  
2.  Arrêtez le profileur.  Type :  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(Facultatif\) Désactivez les variables d'environnement de profilage.  Type :  
  
     **VSPerfCmd \/globaloff**  
  
4.  Redémarrez l'ordinateur.  Si nécessaire, redémarrez les services Internet \(IIS\).  Type :  
  
     **IISReset \/start**  
  
## Voir aussi  
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)