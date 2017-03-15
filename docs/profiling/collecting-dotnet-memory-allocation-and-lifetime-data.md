---
title: "Collecte de donn&#233;es li&#233;es &#224; l’allocation et &#224; la dur&#233;e de vie de la m&#233;moire .NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "profilage de la mémoire .NET, méthode"
  - "outils de profilage, méthode de mémoire .NET"
ms.assetid: 62a6dd5f-db66-4456-9d57-f8913dbfe4d5
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Collecte de donn&#233;es li&#233;es &#224; l’allocation et &#224; la dur&#233;e de vie de la m&#233;moire .NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prennent en charge les données d'allocation de mémoire et de durée de vie des objets .NET pour vous permettre de détecter des problèmes de performances relatifs à la mémoire dans votre application.  
  
-   Les données liées à l'allocation de mémoire .NET incluent la taille et le nombre des objets liés à la mémoire .NET Framework qui ont été alloués.  
  
-   Les informations de durée de vie des objets incluent la taille et le nombre des objets liés à la mémoire .NET Framework qui ont été libérés lors des trois générations de garbage collection.  
  
 **Conditions requises**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans Windows 8 et Windows Server 2012 nécessitaient d'importantes modifications de la manière dont le profileur Visual Studio collecte des données sur ces plateformes.  Les applications Windows Store requièrent également de nouvelles techniques de collecte.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Vous pouvez collecter des données à l'aide de la méthode d'échantillonnage ou de profilage par instrumentation.  
  
-   Lorsque vous utilisez la méthode d'échantillonnage, le profileur suit toutes les allocations de mémoire .NET et les objets qui ont été générés par le processus qui a été démarré ou attaché.  
  
-   Lorsque vous utilisez la méthode d'instrumentation, le profileur suit uniquement ces allocations de mémoire .NET et objets générés par les modules instrumentés.  
  
> [!IMPORTANT]
>  Lorsque vous collectez des données de mémoire .NET \(allocations, durées de vie d'objet, ou les deux\) à l'aide de la méthode d'échantillonnage, tous les événements d'échantillonnage spécifiés par l'utilisateur sont ignorés et les allocations de mémoire appropriées et\/ou les événements d'allocation de mémoire sont utilisés pour collecter les données.  
  
 Si vous activez le profilage de l'allocation de mémoire .NET, vous activez également le mode Allocation.  Si vous activez le profilage de données de durée de vie du .NET, vous activez également le mode Durée de vie des objets.  Pour plus d’informations, consultez [Mode Allocations](../profiling/dotnet-memory-allocations-view.md) et [Mode Durée de vie de l'objet](../profiling/object-lifetime-view.md).  
  
 Pour plus d'informations sur la façon de collecter les données de mémoire .NET à l'aide des outils en ligne de commande des outils de profilage, consultez Utilisation des méthodes de mémoire .NET pour collecter des données d'allocation de mémoire et de durée de vie des objets dans [Utilisation de méthodes de profilage à partir de la ligne de commande](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).  
  
### Pour collecter les données de la mémoire .NET  
  
1.  Dans l'**Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue**Pages de propriétés** de la *Performance Session*, cliquez sur l'onglet **Général**, puis activez la case à cocher **Collecter les informations d'allocation d'objets .NET**.  
  
3.  Pour collecter les données de durée de vie des objets .NET, activez la case à cocher **Collecter aussi les informations de durée de vie des objets .NET**.  
  
## Tâches courantes  
 Spécifiez des options supplémentaires dans la boîte de dialogue **Pages de propriétés** de la *Performance Session*.  Pour ouvrir cette boîte de dialogue :  
  
-   Dans l'**Explorateur de performances**, cliquez avec le bouton droit sur le nom de la session de performance, puis cliquez sur **Propriétés**.  
  
 Les tâches figurant dans le tableau suivant décrivent des options que vous pouvez spécifier dans la boîte de dialogue **Pages de propriétés** de *Performance Session* lorsque vous collectez les données de mémoire .NET.  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|Sur la page **Général**, spécifiez les détails d'attribution de nom pour le fichier de données de profilage généré \(.vsp\).|-   [Collecting .NET Memory Allocation and Lifetime Data](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Comment : définir les options de nom de fichier de données de profilage](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Sur la page **Lancement**, choisissez l'application à démarrer si votre solution de code comporte plusieurs projets .exe.|-   [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)|  
|Dans la page **Interactions de couche**, ajoutez les données d'appel ADO.NET à l'exécution du profilage.|-   [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)|  
|Sur la page **Événements Windows**, spécifiez un ou plusieurs événements de Suivi d'événements pour Windows \(ETW\) à collecter avec les données d'échantillonnage.|-   [Comment : collecter les données de suivi d’événements pour Windows \(ETW\)](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)|  
|Dans la page **Compteurs Windows**, spécifiez un ou plusieurs compteurs de performance de système d'exploitation à ajouter aux données de profilage en tant que marques.|-   [Comment : collecter les données des compteurs Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Sur la page **Avancé**, spécifiez la version du runtime .NET Framework à profiler si vos modules d'application utilisent plusieurs versions.  Par défaut, la première version chargée est profilée.|-   [Comment : spécifier le runtime .NET Framework à profiler dans les scénarios côte à côte](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)|  
  
## Tâches d'instrumentation  
 Les tâches figurant dans le tableau suivant sont des options de la boîte de dialogue **Pages de propriétés** qui sont spécifiques au profilage avec la méthode d'instrumentation.  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|Sur la page **Fichiers binaires**, spécifiez un emplacement pour les copies instrumentées des modules.  Par défaut, les fichiers binaires d'origine sont déplacés dans un dossier de sauvegarde.|-   [Comment : déplacer des binaires instrumentés](../profiling/how-to-relocate-instrumented-binaries.md)|  
|Sur la page **Instrumentation**, excluez les petites fonctions du profilage pour réduire les surcharges de profilage, profilez le code JavaScript dans les pages Web ASP.NET et spécifiez les commandes à exécuter à une invite de commandes avant et après le processus d'instrumentation.|-   [Procédure : exclure ou inclure les fonctions courtes de l’instrumentation](../Topic/How%20to:%20Exclude%20or%20Include%20Short%20Functions%20from%20Instrumentation.md)<br />-   [Comment : profiler du code JavaScript \(ECMA\) dans des pages web](../Topic/How%20to:%20Profile%20JavaScript%20Code%20in%20Web%20Pages.md)<br />-   [Comment : spécifier des commandes de pré\-instrumentation et de post\-instrumentation](../Topic/How%20to:%20Specify%20Pre-%20and%20Post-Instrument%20Commands.md)|  
|Sur la page **Compteurs UC**, spécifiez un ou plusieurs compteurs de performance du processeur à ajouter aux données de profilage.|-   [Comment : collecter les données des compteurs UC](../profiling/how-to-collect-cpu-counter-data.md)|  
|Sur la page **Options avancées**, spécifiez les options VSInstr.exe supplémentaires souhaitées, notamment les options permettant d'inclure ou d'exclure des fonctions spécifiques.  Pour plus d'informations sur ces options VSInstr, consultez [VSInstr](../profiling/vsinstr.md).|-   [Comment : spécifier des options d’instrumentation supplémentaires](../Topic/How%20to:%20Specify%20Additional%20Instrumentation%20Options.md)<br />-   [Comment : limiter l’instrumentation à des fonctions spécifiques](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|  
  
## Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Comment : choisir des méthodes de collection](../profiling/how-to-choose-collection-methods.md)   
 [Propriétés d’une session de performance](../profiling/performance-session-properties.md)