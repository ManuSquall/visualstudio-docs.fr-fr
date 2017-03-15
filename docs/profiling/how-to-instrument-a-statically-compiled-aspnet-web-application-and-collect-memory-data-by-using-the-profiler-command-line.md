---
title: "Comment&#160;: instrumenter une application Web ASP.NET compil&#233;e statiquement et collecter des donn&#233;es de m&#233;moire en utilisant la ligne de commande du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: instrumenter une application Web ASP.NET compil&#233;e statiquement et collecter des donn&#233;es de m&#233;moire en utilisant la ligne de commande du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique explique comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour instrumenter un composant Web ou un site Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] précompilé et collecter des données d'allocation de mémoire .NET, de durée de vie d'objet et de temporisation détaillées.  
  
> [!NOTE]
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] s  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre d'invite de commandes ou l'ajouter à la commande elle\-même.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Pour collecter les données d'un composant Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] à l'aide de la méthode d'instrumentation, utilisez l'outil [VSInstr.exe](../profiling/vsinstr.md) pour générer une version instrumentée du composant.  Sur l'ordinateur qui héberge le composant, remplacez la version non instrumentée du composant par la version instrumentée.  Utilisez ensuite l'outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d'environnement de profilage globales et redémarrer l'ordinateur hôte.  Vous démarrez alors le profileur.  
  
 Lorsque le composant instrumenté est exécuté, les données de minutage sont automatiquement collectées dans un fichier de données.  Vous pouvez suspendre et reprendre la collecte de données pendant la session de profilage.  
  
 Pour terminer une session de profilage, fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] qui héberge le composant, puis arrêtez explicitement le profileur.  Dans la plupart des cas, nous vous recommandons de désactiver les variables d'environnement de profilage à la fin d'une session.  
  
## Début du profilage  
  
#### Pour instrumenter un composant Web ASP.NET et commencer le profilage  
  
1.  Utilisez l'outil **VSInstr** pour générer une version instrumentée de l'application cible.  Si nécessaire, remplacez les binaires d'application sur l'ordinateur hôte ASP.NET par les binaires instrumentés.  
  
2.  Ouvrez une fenêtre d'invite de commandes.  
  
3.  Initialisez les variables d'environnement de profilage .NET.  Dans une fenêtre d'invite de commandes, tapez :  
  
     **VSPerfClrEnv \/globaltracegc**  
  
     ou  
  
     **VSPerfClrEnv \/globaltracegclife**  
  
    -   **\/globaltracegc** collecte les données d'allocation de mémoire .NET et de temporisation.  
  
    -   **\/globaltracegclife** collecte les données d'allocation de mémoire .NET, de durée de vie d'objet, ainsi que des données de temporisation détaillées.  
  
4.  Redémarrez l'ordinateur.  
  
5.  Ouvrez une fenêtre d'invite de commandes.  
  
6.  Démarrez le profileur.  Dans une fenêtre d'invite de commandes, tapez :  
  
     **VSPerfCmd \/start:trace \/output:**`OutputFile` \[`Options`\]  
  
    -   L'option [\/start](../profiling/start.md)**:trace** initialise le profileur.  
  
    -   L'option [\/output](../profiling/output.md)**:**`OutputFile` est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser n'importe laquelle des options suivantes avec l'option **\/start:trace**.  
  
    > [!NOTE]
    >  Les options **\/user** et **\/crosssession** sont généralement requises pour les applications ASP.NET.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Spécifie le domaine et le nom d'utilisateur facultatifs du compte qui possède le processus de travail ASP.NET.  Cette option est requise si le processus s'exécute via un compte d'utilisateur différent de celui de l'utilisateur qui a ouvert la session. Le nom est répertorié dans la colonne Nom d'utilisateur sous l'onglet Processus du Gestionnaire des tâches Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Active le profilage de processus dans d'autres sessions.  Cette option est requise si l'application s'exécute dans une session différente.  L'identificateur de session est répertorié dans la colonne Identificateur de session sous l'onglet Processus du Gestionnaire des tâches de Windows.  **\/CS** peut être spécifié en tant qu'abréviation de **\/crosssession**.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est de 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie un événement ETW \(Event Tracing for Windows\) à collecter au cours du profilage.  Les événements ETW sont collectés dans un fichier séparé \(.etl\).|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Pour démarrer le profileur avec la collecte de données en pause, ajoutez l'option **\/globaloff** à la ligne de commande **\/start**.  Utilisez **\/globalon** pour reprendre le profilage.|  
  
7.  Ouvrez le site Web qui contient le composant instrumenté.  
  
## Contrôle de la collecte de données  
 Lorsque l'application cible s'exécute, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l'écriture de données dans le fichier à l'aide des options **VSPerfCmd.exe**.  Le contrôle de la collecte de données vous permet de collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
#### Pour démarrer et arrêter la collecte de données  
  
-   Les paires suivantes d'options démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Démarre \(**\/globalon**\) ou arrête \(**\/globaloff**\) la collecte de données pour tous les processus.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Démarre \(**\/processon**\) ou arrête \(**\/processoff**\) la collecte de données pour le processus spécifié par l'ID de processus \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Démarre \(**\/threadon**\) ou arrête \(**\/threadoff**\) la collecte de données pour le thread spécifié par l'ID de thread \(`TID`\).|  
  
## Fin de la session de profilage  
 Pour terminer une session de profilage, fermez l'application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], puis utilisez la commande Internet Information Services \(IIS\) **IISReset** pour fermer le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Appelez l'option **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) pour arrêter le profileur et fermer le fichier de données de profilage.  La commande **VSPerfClrEnv \/globaloff** désactive les variables d'environnement de profilage.  Vous devez redémarrer l'ordinateur pour que les nouveaux paramètres d'environnement soient appliqués.  
  
#### Pour terminer une session de profilage  
  
1.  Fermez l'application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Type :  
  
     **IISReset \/stop**  
  
3.  Arrêtez le profileur.  Type :  
  
     **VSPerfCmd \/shutdown**  
  
4.  \(Facultatif\).  Désactivez les variables d'environnement de profilage.  Type :  
  
     **VSPerfCmd \/globaloff**  
  
5.  Redémarrez l'ordinateur.  Si nécessaire, redémarrez IIS.  Type :  
  
     **IISReset \/start**  
  
## Voir aussi  
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)