---
title: "Comment&#160;: attacher le profileur &#224; une application .NET Framework autonome pour collecter des donn&#233;es de m&#233;moire en utilisant la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a869fa4-3c98-4e08-b5d9-f43523059f0e
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: attacher le profileur &#224; une application .NET Framework autonome pour collecter des donn&#233;es de m&#233;moire en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique explique comment utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] pour attacher le profileur à une application \(cliente\) autonome du .NET Framework en cours d'exécution, puis collecter des données de mémoire.  
  
> [!NOTE]
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous\-répertoire \\Team Tools\\Performance Tools du répertoire d'installation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] s  Sur les ordinateurs 64 bits, les versions 64 bits et 32 bits de ces outils sont disponibles.  Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin d'accès des outils à la variable d'environnement PATH de la fenêtre Invite de commandes ou l'ajouter à la commande elle\-même.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Pour attacher le profileur à une application .NET Framework et collecter les données de mémoire, vous devez utiliser l'outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d'environnement appropriées avant le démarrage de l'application cible.  Une fois le profileur attaché à l'application, vous pouvez utiliser l'outil **VSPerfCmd.exe** pour suspendre et reprendre la collecte de données.  
  
 Pour terminer une session de profilage, le profileur doit être détaché de tous les processus profilés et arrêté explicitement.  Dans la plupart des cas, nous vous recommandons de désactiver les variables d'environnement de profilage à la fin d'une session.  
  
## Attachement du profileur  
  
#### Pour attacher le profileur à une application .NET Framework en cours d'exécution  
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Initialisez les variables d'environnement de profilage.  Type :  
  
     **VSPerfClrEnv** {**\/samplegc** &#124; **\/samplegclife**} \[**\/samplelineoff**\]  
  
    -   Les options **\/samplegc** et **\/samplegclife** indiquent s'il faut collecter des données d'allocation de mémoire uniquement, ou collecter à la fois les données d'allocation de mémoire et de durée de vie de l'objet.  Vous ne pouvez spécifier qu'une seule et unique option.  
  
        |Option|Descriptions|  
        |------------|------------------|  
        |**\/samplegc**|Collecte uniquement les données d'allocation de mémoire.|  
        |**\/samplegclife**|Collecte les données d'allocation de la mémoire et de durée de vie des objets.|  
  
    -   L'option **\/samplelineoff** désactive la collection de données de numéros de ligne du code source.  
  
3.  Démarrez le profileur.  Type :  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   L'option [\/start](../profiling/start.md)**:sample** initialise le profileur.  
  
    -   L'option [\/output](../profiling/output.md)**:**`OutputFile` est requise avec **\/start**.  `OutputFile` spécifie le nom et l'emplacement du fichier de données de profilage \(.vsp\).  
  
     Vous pouvez utiliser n'importe laquelle des options suivantes avec l'option **\/start:sample**.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Spécifie le domaine et le nom d'utilisateur du compte qui possède le processus profilé.  Cette option est uniquement requise si le processus s'exécute en tant qu'utilisateur autre que l'utilisateur connecté.  Le propriétaire du processus est répertorié dans la colonne Nom d'utilisateur sous l'onglet Processus du Gestionnaire des tâches de Windows.|  
    |[\/crosssession &#124; \/cs](../profiling/crosssession.md)|Active le profilage de processus dans d'autres sessions.  Cette option est requise si l'application s'exécute dans une session différente.  L'identificateur de session est répertorié dans la colonne Identificateur de session sous l'onglet Processus du Gestionnaire des tâches de Windows.  **\/CS** peut être spécifié en tant qu'abréviation de **\/crosssession**.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie un compteur de performance Windows à collecter au cours du profilage.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|À n'utiliser qu'avec **\/wincounter**.  Spécifie le nombre de millisecondes entre les événements de collecte du compteur de performance Windows.  La valeur par défaut est de 500 ms.|  
  
4.  Si nécessaire, démarrez l'application cible de la manière habituelle.  
  
5.  Attachez le profileur à l'application cible.  Type :  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   `PID` spécifie l'ID de processus de l'application cible.  `ProcessName` spécifie le nom du processus.  Notez que si vous spécifiez `ProcessName` et que plusieurs processus du même nom sont en cours d'exécution, les résultats sont imprévisibles.  Vous pouvez afficher les ID de processus de tous les processus en cours d'exécution dans le Gestionnaire des tâches de Windows.  
  
    -   **\/targetclr:** `Version` spécifie la version du Common Language Runtime \(CLR\) à profiler lorsque plusieurs versions du runtime sont chargées dans une application.  Optionnel.  
  
## Contrôle de la collecte de données  
 Lorsque l'application cible s'exécute, vous pouvez contrôler la collecte de données en démarrant et en arrêtant l'écriture de données dans le fichier à l'aide des options **VSPerfCmd.exe**.  Le contrôle de la collecte de données vous permet de collecter des données pour une partie spécifique de l'exécution du programme, notamment le démarrage ou l'arrêt de l'application.  
  
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
  
     **VSPerfCmd \/off**  
  
## Voir aussi  
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)