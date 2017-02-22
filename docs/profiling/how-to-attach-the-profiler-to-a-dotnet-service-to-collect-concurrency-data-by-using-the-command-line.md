---
title: "Comment&#160;: attacher le profileur &#224; un service .NET pour collecter des donn&#233;es de concurrence en utilisant la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: attacher le profileur &#224; un service .NET pour collecter des donn&#233;es de concurrence en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique explique comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à un service [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] et collecter des données de concurrence de processus et de threads à l'aide de la méthode d'échantillonnage.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans Windows 8 et Windows Server 2012 nécessitaient d'importantes modifications de la manière dont le profileur Visual Studio collecte des données sur ces plateformes.  Les applications Windows Store requièrent également de nouvelles techniques de collecte.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Les outils de ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de Visual Studio  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre Invite de commandes ou l'ajouter à la commande elle\-même.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Pour collecter des données d'accès concurrentiel, attachez le profileur au processus de service.  Lorsque le profileur est attaché au service, vous pouvez suspendre la collecte de données et la reprendre.  Pour terminer une session de profilage, le profileur ne doit plus être attaché au service et doit être arrêté explicitement.  Dans la plupart des cas, nous vous recommandons de désactiver les variables d'environnement de profilage à la fin d'une session.  
  
## Attachement du profileur  
  
#### Pour attacher le profileur à un service .NET Framework  
  
1.  Installez le service.  
  
2.  Ouvrez une fenêtre d'invite de commandes.  
  
3.  Initialisez les variables d'environnement de profilage.  Type :  
  
     [VSPerfClrEnv](../profiling/vsperfclrenv.md) **\/globalsampleon** \[**\/samplelineoff**\]  
  
    -   **\/globalsampleon** active l'échantillonnage.  
  
    -   **\/samplelineoff** désactive l'assignation des données collectées à des lignes de code source spécifiques.  Lorsque cette option est spécifiée, les données sont assignées uniquement aux fonctions.  
  
4.  Redémarrez l'ordinateur.  
  
5.  Démarrez le profileur.  Type :  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
     L'option [\/output](../profiling/output.md)**:**`OutputFile` est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser n'importe laquelle des options suivantes avec l'option **\/start**.  
  
    > [!NOTE]
    >  Les options **\/user** et **\/crosssession** sont généralement requises pour les services.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Spécifie le domaine et le nom d'utilisateur du compte qui possède le processus profilé.  Cette option est uniquement requise si le processus s'exécute en tant qu'un utilisateur autre que l'utilisateur connecté.  Le propriétaire du processus est répertorié dans la colonne Nom d'utilisateur sous l'onglet Processus du Gestionnaire des tâches de Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Active le profilage de processus dans d'autres sessions.  Cette option est obligatoire si le service s'exécute dans une session différente.  L'identificateur de session est répertorié dans la colonne Identificateur de session sous l'onglet Processus du Gestionnaire des tâches de Windows.  **\/CS** peut être spécifié en tant qu'abréviation de **\/crosssession**.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est de 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie un événement ETW \(Event Tracing for Windows\) à collecter au cours du profilage.  Les événements ETW sont collectés dans un fichier séparé \(.etl\).|  
  
6.  Si nécessaire, démarrez le service.  
  
7.  Attachez le profileur au service.  Type :  
  
     **VSPerfCmd \/attach:** `PID` \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   `PID` spécifie l'ID ou le nom de processus du service.  Vous pouvez afficher les ID de processus de tous les processus en cours d'exécution dans le Gestionnaire des tâches de Windows.  
  
    -   **targetclr:** `Version` spécifie la version du Common Language Runtime \(CLR\) à profiler lorsque plusieurs versions du runtime sont chargées dans une application.  Optionnel.  
  
## Contrôle de la collecte de données  
 Lorsque le service s'exécute, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l'écriture de données dans le fichier à l'aide des options VSPerfCmd.exe.  Le contrôle de la collecte de données vous permet de collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
#### Pour démarrer et arrêter la collecte de données  
  
-   Les paires suivantes d'options **VSPerfCmd** démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Démarre \(**\/globalon**\) ou arrête \(**\/globaloff**\) la collecte de données pour tous les processus.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Démarre \(**\/processon**\) ou arrête \(**\/processoff**\) la collecte de données pour le processus spécifié par l'ID de processus \(`PID`\).|  
    |**\/attach:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[:{`PID`&#124;`ProcName`}\]|**\/attach** commence à collecter des données pour le processus spécifié par l'ID de processus ou le nom de processus.  **\/detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus n'est spécifié.|  
  
-   Vous pouvez également utiliser l'option **VSPerfCmd.exe** [\/mark](../profiling/mark.md) pour insérer une marque de profilage dans le fichier de données.  La commande **\/mark** ajoute un identificateur, un horodatage et une chaîne de texte facultative définie par l'utilisateur.  Les marques peuvent servir à filtrer les données dans les rapports et les vues de données du profileur.  Les paires d'options VSPerfCmd suivantes démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
## Fin de la session de profilage  
 Pour terminer une session de profilage, le profileur ne doit pas collecter des données.  Vous pouvez cesser de collecter les données d'une application profilée avec la méthode de concurrence en arrêtant le service ou en appelant l'option **VSPerfCmd \/detach**.  Vous appelez alors l'option **VSPerfCmd \/shutdown** pour arrêter le profileur et fermer le fichier de données de profilage.  La commande **VSPerfClrEnv \/globaloff** désactive les variables d'environnement de profilage, mais la configuration du système n'est réinitialisée qu'au redémarrage de l'ordinateur.  
  
#### Pour terminer une session de profilage  
  
1.  Effectuez l'une des opérations suivantes pour détacher le profileur de l'application cible.  
  
    -   Arrêtez le service.  
  
         ou  
  
    -   Tapez **VSPerfCmd \/detach.**  
  
2.  Arrêtez le profileur.  Type :  
  
     **VSPerfCmd**  [Shutdown](../profiling/shutdown.md)