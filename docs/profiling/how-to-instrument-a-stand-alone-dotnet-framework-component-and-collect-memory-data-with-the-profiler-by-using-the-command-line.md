---
title: "Comment&#160;: instrumenter un composant .NET Framework autonome et collecter des donn&#233;es de m&#233;moire avec le profileur en utilisant la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: instrumenter un composant .NET Framework autonome et collecter des donn&#233;es de m&#233;moire avec le profileur en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique explique comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour instrumenter un composant .NET Framework d'une application autonome tel qu'un fichier .exe ou .dll et collecter des informations de mémoire à l'aide du profileur.  
  
> [!NOTE]
>  Les outils de ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de Visual Studio  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre Invite de commandes ou l'ajouter à la commande elle\-même.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Pour collecter les données de mémoire d'un composant .NET Framework à l'aide de la méthode d'instrumentation, utilisez l'outil [VSInstr.exe](../profiling/vsinstr.md) pour générer une version instrumentée du composant et l'outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d'environnement de profilage.  Démarrez ensuite le profileur à l'aide de l'outil **VSPerfCmd.exe**.  
  
 Lorsque le composant instrumenté est exécuté, les données de mémoire sont automatiquement collectées dans un fichier de données.  Vous pouvez suspendre et reprendre la collecte de données pendant la session de profilage.  
  
 Pour terminer une session de profilage, fermez l'application cible et arrêtez explicitement le profileur.  Dans la plupart des cas, nous vous recommandons de désactiver les variables d'environnement de profilage à la fin d'une session.  
  
## Démarrage de l'application avec le profileur  
  
#### Pour attacher le profileur à une application .NET Framework en cours d'exécution  
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Utilisez l'outil **VSInstr** pour générer une version instrumentée de l'application cible.  
  
3.  Initialisez les variables d'environnement de profilage .NET Framework.  Type :  
  
     **VSPerfClrEnv** {**\/tracegc** &#124; **\/tracegclife**}  
  
    -   Les options **\/tracegc** et **\/tracegclife** initialisent les variables d'environnement pour collecter les données d'allocation de mémoire uniquement, ou collecter à la fois les données d'allocation de mémoire et de durée de vie des objets.  
  
        |Option|Description|  
        |------------|-----------------|  
        |**\/tracegc**|Active la collecte des données d'allocation de mémoire uniquement.|  
        |**\/tracegclife**|Active la collecte des données d'allocation de mémoire et des données de durée de vie des objets.|  
  
4.  Démarrez le profileur.  Type :  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   L'option [\/start](../profiling/start.md)**:trace** initialise le profileur.  
  
    -   L'option [\/output](../profiling/output.md)**:**`OutputFile` est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser n'importe laquelle des options suivantes avec l'option **\/start:trace**.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Spécifie le domaine et le nom d'utilisateur du compte qui possède le processus profilé.  Cette option est uniquement requise si le processus s'exécute en tant qu'utilisateur autre que l'utilisateur connecté.  Le propriétaire du processus est répertorié dans la colonne Nom d'utilisateur sous l'onglet Processus du Gestionnaire des tâches de Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Active le profilage de processus dans d'autres sessions.  Cette option est requise si l'application s'exécute dans une session différente.  L'identificateur de session est répertorié dans la colonne Identificateur de session sous l'onglet Processus du Gestionnaire des tâches de Windows.  **\/CS** peut être spécifié en tant qu'abréviation de **\/crosssession**.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Pour démarrer le profileur avec la collecte de données en pause, ajoutez l'option **\/globaloff** à la ligne de commande **\/start**.  Utilisez **\/globalon** pour reprendre le profilage.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est de 500 ms.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Collecte les informations du compteur de performance de processeur spécifié dans Config.  Des informations de compteur sont ajoutées aux données collectées à chaque événement de profilage.|  
    |[events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie un événement ETW \(Event Tracing for Windows\) à collecter au cours du profilage.  Les événements ETW sont collectés dans un fichier séparé \(.etl\).|  
  
5.  Démarrez l'application cible à partir de la fenêtre d'invite de commandes.  
  
## Contrôle de la collecte de données  
 Lorsque l'application cible s'exécute, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l'écriture de données dans le fichier à l'aide des options **VSPerfCmd.exe**.  Le contrôle de la collecte de données vous permet de collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
#### Pour démarrer et arrêter la collecte de données  
  
-   Les paires suivantes d'options **VSPerfCmd** démarrent et arrêtent la collecte de données.  Spécifiez chaque option sur une ligne de commande séparée.  Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/globalon](../profiling/globalon-and-globaloff.md) [\/globaloff](../profiling/globalon-and-globaloff.md)|Démarre \(**\/globalon**\) ou arrête \(**\/globaloff**\) la collecte de données pour tous les processus.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Démarre \(**\/processon**\) ou arrête \(**\/processoff**\) la collecte de données pour le processus spécifié par l'ID de processus \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Démarre \(**\/threadon**\) ou arrête \(**\/threadoff**\) la collecte de données pour le thread spécifié par l'ID de thread \(`TID`\).|  
  
## Fin de la session de profilage  
 Pour terminer une session de profilage, fermez l'application qui exécute le composant instrumenté, puis appelez l'option **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) pour désactiver le profileur et fermer le fichier de données de profilage.  La commande **VSPerfClrEnv \/off** désactive les variables d'environnement de profilage.  
  
#### Pour terminer une session de profilage  
  
1.  Fermez l'application cible.  
  
2.  Arrêtez le profileur.  Type :  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(Facultatif\) Désactivez les variables d'environnement de profilage.  Type :  
  
     **VSPerfCmd \/off**  
  
## Voir aussi  
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)