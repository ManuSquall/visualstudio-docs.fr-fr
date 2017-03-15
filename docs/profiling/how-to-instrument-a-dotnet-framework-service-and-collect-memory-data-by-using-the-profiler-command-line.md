---
title: "Comment&#160;: instrumenter un service .NET Framework et collecter des donn&#233;es de m&#233;moire en utilisant la ligne de commande du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: instrumenter un service .NET Framework et collecter des donn&#233;es de m&#233;moire en utilisant la ligne de commande du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour instrumenter un service [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] et collecter des données d'utilisation de la mémoire.  Vous pouvez collecter des données d'allocation de mémoire, ou vous pouvez collecter à la fois des données d'allocation de mémoire et de durée de vie des objets.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans Windows 8 et Windows Server 2012 nécessitaient d'importantes modifications de la manière dont le profileur Visual Studio collecte des données sur ces plateformes.  Les applications Windows Store requièrent également de nouvelles techniques de collecte.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Vous ne pouvez pas profiler un service avec la méthode d'instrumentation si le service ne peut pas être redémarré après le démarrage de l'ordinateur, type de service qui démarre au démarrage du système d'exploitation.  
>   
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] s  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre d'invite de commandes ou l'ajouter à la commande elle\-même.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Démarrage de la session de profilage  
 Pour collecter les données de performance d'un service [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], vous utilisez l'outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d'environnement appropriées et l'outil [VSInstr.exe](../profiling/vsinstr.md) pour créer une copie instrumentée du fichier binaire de service.  
  
 L'ordinateur qui héberge le service doit être redémarré pour être configuré pour le profilage.  Vous devez également démarrer manuellement le service à partir du Gestionnaire de contrôle des services.  Vous démarrez le profileur, puis démarrez le service [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Lorsque le composant instrumenté est exécuté, les données de mémoire sont automatiquement collectées dans un fichier de données.  Vous pouvez suspendre et reprendre la collecte de données pendant la session de profilage.  
  
 Pour terminer une session de profilage, vous fermez le service et arrêtez explicitement le profileur.  Dans la plupart des cas, nous vous recommandons de désactiver les variables d'environnement de profilage à la fin d'une session.  
  
#### Pour commencer à profiler un service .NET Framework  
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Utilisez l'outil **VSInstr** pour générer une version instrumentée du binaire de service.  
  
3.  Utilisez le Gestionnaire de contrôle des services pour remplacer la version binaire d'origine par la version instrumentée.  Assurez\-vous que le type de démarrage du service a la valeur Manuel.  
  
4.  Initialisez les variables d'environnement de profilage.  Type :  
  
     **VSPerfClrEnv** {**\/globaltracegc** &#124; **\/globaltracegclife**}  
  
    -   **\/globaltracegc** et **\/globaltracegclife** activent la collecte des données d'allocation de mémoire et de durée de vie des objets.  
  
        |Option|Description|  
        |------------|-----------------|  
        |**\/globaltracegc**|Collecte uniquement les données d'allocation de mémoire.|  
        |**\/globaltracegclife**|Collecte les données d'allocation de mémoire et de durée de vie des objets.|  
  
5.  Redémarrez l'ordinateur.  
  
6.  Ouvrez une fenêtre d'invite de commandes.  
  
7.  Démarrez le profileur.  Type :  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:trace**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   L'option **\/start: contention** initialise le profileur.  
  
    -   L'option **\/output:**`OutputFile` est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser n'importe laquelle des options suivantes avec l'option **\/start:sample**.  
  
    > [!NOTE]
    >  Les options **\/user** et **\/crosssession** sont généralement requises pour les services.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Spécifie le domaine et le nom d'utilisateur du compte qui possède le processus de travail ASP.NET.  Cette option est requise si le processus s'exécute en tant qu'un utilisateur autre que l'utilisateur connecté.  Le propriétaire du processus est répertorié dans la colonne Nom d'utilisateur sous l'onglet Processus du Gestionnaire des tâches de Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Active le profilage de processus dans d'autres ouvertures de session.  Cette option est requise si l'application ASP.NET s'exécute dans une session différente.  L'identificateur de session est répertorié dans la colonne Identificateur de session sous l'onglet Processus du Gestionnaire des tâches de Windows.  **\/CS** peut être spécifié en tant qu'abréviation de **\/crosssession**.|  
    |[\/waitstart](../profiling/waitstart.md)\[**:**`Interval`\]|Spécifie le nombre de secondes d'attente lors de l'initialisation du profileur avant qu'une erreur ne soit retournée.  Si `Interval` n'est pas spécifié, le profileur attend indéfiniment.  Par défaut, **\/start** est immédiatement retourné.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Pour démarrer le profileur avec la collecte de données en pause, ajoutez l'option **\/globaloff** à la ligne de commande **\/start**.  Utilisez **\/globalon** pour reprendre le profilage.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Collecte des informations du compteur de performance de processeur spécifié dans Config.  Des informations de compteur sont ajoutées aux données collectées à chaque événement de profilage.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est de 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie un événement ETW \(Event Tracing for Windows\) à collecter au cours du profilage.  Les événements ETW sont collectés dans un fichier séparé \(.etl\).|  
  
8.  Si nécessaire, démarrez le service.  
  
9. Attachez le profileur au service.  Type :  
  
     **VSPerfCmd \/attach:** `PID` &#124;`ProcessName`  
  
    -   Spécifiez l'ID de processus ou le nom de processus du service.  Vous pouvez afficher les ID et les noms de processus de tous les processus en cours d'exécution dans le Gestionnaire des tâches de Windows.  
  
## Contrôle de la collecte de données  
 Lorsque le service s'exécute, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l'écriture de données dans le fichier à l'aide des options **VSPerfCmd.exe**.  Le contrôle de la collecte de données vous permet de collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
#### Pour démarrer et arrêter la collecte de données  
  
-   Les paires suivantes d'options **VSPerfCmd** démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Démarre \(**\/globalon**\) ou arrête \(**\/globaloff**\) la collecte de données pour tous les processus.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [\/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Démarre \(**\/processon**\) ou arrête \(**\/processoff**\) la collecte de données pour le processus spécifié par l'ID de processus \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID`  [\/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Démarre \(**\/threadon**\) ou arrête \(**\/threadoff**\) la collecte de données pour le thread spécifié par l'ID de thread \(`TID`\).|  
  
## Fin de la session de profilage  
 Pour terminer une session de profilage, fermez l'application qui exécute le composant instrumenté, puis démarrez l'option **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) pour désactiver le profileur et fermer le fichier de données de profilage.  La commande **VSPerfClrEnv \/globaloff** désactive les variables d'environnement de profilage.  
  
#### Pour terminer une session de profilage  
  
1.  Arrêtez le service à partir du Gestionnaire de contrôle des services.  
  
2.  Arrêtez le profileur.  Type :  
  
     **VSPerfCmd \/shutdown**  
  
3.  Une fois que vous avez terminé le profilage, effacez les variables d'environnement de profilage.  Type :  
  
     **VSPerfClrEnv \/globaloff**  
  
     Remplacez le module instrumenté par le module d'origine.  Si nécessaire, reconfigurez le type de démarrage du service.  
  
4.  Redémarrez l'ordinateur.  
  
## Voir aussi  
 [Profilage de services](../profiling/command-line-profiling-of-services.md)   
 [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)