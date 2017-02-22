---
title: "Comment&#160;: instrumenter une application Web ASP.NET compil&#233;e dynamiquement et collecter des donn&#233;es de m&#233;moire en utilisant la ligne de commande du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: instrumenter une application Web ASP.NET compil&#233;e dynamiquement et collecter des donn&#233;es de m&#233;moire en utilisant la ligne de commande du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour collecter des données d'allocation de mémoire .NET détaillées et de durée de vie des objets pour une application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dynamiquement compilée à l'aide de la méthode de profilage par instrumentation.  
  
> [!NOTE]
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] s  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre d'invite de commandes ou l'ajouter à la commande elle\-même.  Pour plus d’informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Pour collecter les données de performance d'une application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], vous modifiez le fichier web.config de l'application cible pour permettre à l'outil [VSInstr.exe](../profiling/vsinstr.md) d'instrumenter les fichiers d'application dynamiquement compilés.  Vous utilisez alors l'outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour configurer le serveur qui héberge l'application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] et activez les profilage de la mémoire .NET en définissant les variables d'environnement appropriées, puis redémarrez l'ordinateur.  
  
 Pour collecter des données, démarrez le profileur puis exécutez l'application cible.  Pendant que le profileur est attaché à l'application, vous pouvez suspendre et reprendre la collecte de données. Lorsque vous avez collecté les données appropriées, fermez l'application, fermez le processus de travail des services IIS \(Internet Information Services\), puis arrêtez le profileur.  
  
 Lorsque vous avez terminé votre travail de profilage, restaurez l'état d'origine du fichier web.config et du serveur Web.  
  
## Configuration de l'application Web ASP.NET et du serveur Web  
  
#### Pour configurer l'application Web ASP.NET et le serveur Web  
  
1.  Modifiez le fichier web.config de l'application cible.  Consultez [Comment : modifier des fichiers Web.Config pour instrumenter et profiler des applications Web ASP.NET compilées dynamiquement](../Topic/How%20to:%20Modify%20Web.Config%20Files%20to%20Instrument%20and%20Profile%20Dynamically%20Compiled%20ASP.NET%20Web%20Applications.md).  
  
2.  Sur l'ordinateur qui héberge l'application Web, ouvrez une fenêtre d'invite de commandes.  
  
3.  Initialisez les variables d'environnement de profilage.  Type :  
  
     **VSPerfClrEnv \/globaltracegc**  
  
     ou  
  
     **VSPerfClrEnv \/globaltracegclife**  
  
    -   **\/globaltracegc** active la collecte des données d'allocation de mémoire.  
  
    -   **\/globaltracegclife** active la collecte des données d'allocation de mémoire et des données de durée de vie des objets.  
  
4.  Redémarrez l'ordinateur.  
  
## Exécution de la session de profilage  
  
#### Pour profiler l'application Web ASP.NET  
  
1.  Démarrez le profileur.  Type :  
  
     **VSPerfCmd** [\/start](../profiling/start.md)**:trace** [\/output](../profiling/output.md)**:**`OutputFile` \[`Options`\]  
  
    -   L'option **\/start:trace** initialise le profileur.  
  
    -   L'option **\/output:**`OutputFile` est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser n'importe laquelle des options suivantes avec l'option **\/start:trace**.  
  
    > [!NOTE]
    >  Les options **\/user** et **\/crosssession** sont généralement requises pour les applications ASP.NET.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Spécifie le domaine et le nom d'utilisateur facultatifs du compte qui possède le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Cette option est requise si le processus s'exécute en tant qu'un utilisateur autre que l'utilisateur connecté.  Le nom apparaît dans la colonne Nom d'utilisateur sous l'onglet Processus du Gestionnaire des tâches Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Active le profilage de processus dans d'autres sessions.  Cette option est requise si l'application s'exécute dans une session différente.  L'identificateur de session est répertorié dans la colonne Identificateur de session sous l'onglet Processus du Gestionnaire des tâches de Windows.  **\/CS** peut être spécifié en tant qu'abréviation de **\/crosssession**.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Démarre le profileur avec la collecte de données en pause.  Utilisez [\/globalon](../profiling/globalon-and-globaloff.md) pour reprendre le profilage.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Collecte les informations du compteur de performance de processeur spécifié dans `Config`.  Des informations de compteur sont ajoutées aux données collectées à chaque événement de profilage.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est de 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie un événement ETW \(Event Tracing for Windows\) à collecter au cours du profilage.  Les événements ETW sont collectés dans un fichier séparé \(.etl\).|  
  
2.  Démarrez l'application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de manière classique.  
  
## Contrôle de la collecte de données  
 Lorsque l'application cible s'exécute, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l'écriture de données dans le fichier de données du profileur à l'aide des options **VSPerfCmd.exe**.  Le contrôle de la collecte de données vous permet de collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
#### Pour démarrer et arrêter la collecte de données  
  
-   Les paires suivantes d'options démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Démarre \(**\/globalon**\) ou arrête \(**\/globaloff**\) la collecte de données pour tous les processus.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Démarre \(**\/processon**\) ou arrête \(**\/processoff**\) la collecte de données pour le processus spécifié par l'ID de processus \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Démarre \(**\/threadon**\) ou arrête \(**\/threadoff**\) la collecte de données pour le thread spécifié par l'ID de thread \(`TID`\).|  
  
-   Vous pouvez également utiliser l'option **VSPerfCmd.exe** [\/mark](../profiling/mark.md) pour insérer une marque de profilage dans le fichier de données.  La commande **\/mark** ajoute un identificateur, un horodatage et une chaîne de texte facultative définie par l'utilisateur.  Les marques peuvent servir à filtrer les données dans les rapports et les vues de données du profileur.  
  
## Fin de la session de profilage  
 Pour terminer une session de profilage, fermez l'application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] cible, arrêtez les services IIS \(Internet Information Services\) pour arrêter le processus profilé, puis arrêtez le profileur.  Redémarrez ensuite les services IIS.  
  
#### Pour terminer une session de profilage  
  
1.  Fermez l'application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en réinitialisant les services IIS.  Type :  
  
     **IISReset \/stop**  
  
3.  Arrêtez le profileur.  Type :  
  
     **VSPerfCmd** [\/shutdown](../profiling/shutdown.md)  
  
4.  Redémarrez les services IIS.  Type :  
  
     **IISReset \/start**  
  
## Restauration de l'application et configuration de l'ordinateur  
 Lorsque vous avez terminé tout le profilage, remplacez le fichier web.config, effacez les variables d'environnement de profilage et redémarrez l'ordinateur pour restaurer l'état d'origine du serveur et de l'application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
#### Pour restaurer l'application et la configuration de l'ordinateur  
  
1.  Remplacez le fichier web.config par une copie du fichier d'origine.  
  
2.  \(Facultatif\).  Désactivez les variables d'environnement de profilage.  Type :  
  
     **VSPerfCmd \/globaloff**  
  
3.  Redémarrez l'ordinateur.  
  
## Voir aussi  
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)