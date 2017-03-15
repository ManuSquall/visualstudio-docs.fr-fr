---
title: "Profilage d&#39;applications Windows&#160;8 et Windows Server&#160;2012 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a704215d-d252-4087-921b-ac81ebe2a9c9
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Profilage d&#39;applications Windows&#160;8 et Windows Server&#160;2012
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications Windows Store demandent aussi de nouvelles techniques de collecte. Cette rubrique décrit les modifications concernant le profilage sur les plateformes Windows 8 et Windows Server 2012.  
  
> [!NOTE]
>  Le profilage d’applications sur les autres versions prises en charge de Windows \(Windows 7, Windows Server 2008 R2\) n’a pas évolué.  
  
##  <a name="BKMK_In_this_topic"></a> Dans cette rubrique  
 [Profilage des applications du Windows Store à partir de l'IDE de Visual Studio](#BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE)  
  
 [Profilage des applications qui s'exécutent sur Windows 8 ou sur Windows Server 2012 à partir de l'IDE de Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE)  
  
-   [Profilage des applications qui s'exécutent sur Windows 8 ou sur Windows Server 2012 à l'aide de l'échantillonnage de l'IDE de Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE)  
  
 [Profilage à partir de la ligne de commande](#BKMK_Profiling_from_the_command_line)  
  
 [Collecte des données d'interaction de couche (TIP)](#BKMK_Collecting_tier_interaction__TIP__data)  
  
##  <a name="BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE"></a> Profilage des applications du Windows Store à partir de l'IDE de Visual Studio  
 Quand vous profilez une application du Windows Store écrite en JavaScript et HTML 5, vous collectez des données d’instrumentation pour le code JavaScript. Quand vous profilez une application ou un composant du Windows Store écrit en Visual C\+\+, Visual C\# ou Visual Basic, vous collectez des données d’échantillonnage pour le code natif et managé. Vous pouvez profiler votre application localement ou sur un ordinateur distant.  
  
 Ces fonctionnalités et options de profilage ne sont pas prises en charge quand il s’agit de profiler des applications du Windows Store :  
  
-   profilage d’applications JavaScript à l’aide de la méthode d’échantillonnage ;  
  
-   profilage de code managé et natif à l’aide de la méthode d’instrumentation ;  
  
-   profilage d’accès concurrentiel ;  
  
-   profilage de mémoire .NET ;  
  
-   profilage d’interaction de couche \(TIP\) ;  
  
-   options d’échantillonnage, telles que la définition de l’événement d’échantillonnage et l’intervalle de temporisation, ou la collecte de données de compteurs de performances supplémentaires ;  
  
-   options d’instrumentation, telles que la collecte de données de compteurs de performances et Windows, ou définition d’options de ligne de commande supplémentaires.  
  
 Pour plus d’informations sur le profilage d’applications du Windows Store, consultez les rubriques suivantes dans le Centre de développement Windows :  
  
 [Exécuter des applications du Windows Store sur un ordinateur local](../debugger/run-windows-store-apps-on-the-local-machine.md)  
  
 [Exécuter des applications du Windows Store sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md)  
  
 [Analyser les performances des applications](../Topic/Analyze%20the%20performance%20of%20Windows%20Store%20apps%20using%20Visual%20Studio%20diagnostic%20tools.md)  
  
-   [Collecter des données de minutage de fonction JavaScript sur un ordinateur local](../Topic/JavaScript%20Function%20Timing.md)  
  
-   [Collecter des données de temporisation de fonction JavaScript sur un appareil distant](../Topic/JavaScript%20Function%20Timing%20on%20a%20Remote%20Device.md)  
  
-   [Analyser les données de minutage de fonction JavaScript](../Topic/Analyze%20JavaScript%20Function%20Timing%20data.md)  
  
-   [Profiler du code Visual C\+\+, Visual C\# et Visual Basic dans des applications du Windows Store sur un ordinateur local](http://msdn.microsoft.com/fr-fr/2d0c939e-0bac-48c5-b727-46f6c6113060)  
  
-   [Profiler le code Visual C\+\+, Visual C\# et Visual Basic des applications Windows Store sur un périphérique distant](http://msdn.microsoft.com/fr-fr/b932a2be-11b0-40fd-b996-75c6b6a79d22)  
  
-   [Analyser les données de performances du code Visual C\+\+, Visual C\# et Visual Basic dans des applications Windows Store](http://msdn.microsoft.com/fr-fr/5de4a413-d924-425f-afc4-e1ecfb0fca18)  
  
 [Dans cette rubrique](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE"></a> Profilage des applications qui s'exécutent sur Windows 8 ou sur Windows Server 2012 à partir de l'IDE de Visual Studio  
 Le profilage à l’aide de la méthode d’instrumentation n’a pas évolué pour Windows 8.  
  
 Le profilage d’interaction de couche \(TIP\) n’est pas pris en charge en utilisant la méthode d’échantillonnage.  
  
###  <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE"></a> Profilage des applications qui s'exécutent sur Windows 8 ou sur Windows Server 2012 à l'aide de l'échantillonnage de l'IDE de Visual Studio  
 Ces fonctionnalités et options de profilage ne sont pas prises en charge quand il s’agit de profiler des applications de bureau Windows 8 ou des applications Windows Server 2012 à l’aide de la méthode d’échantillonnage :  
  
-   Profilage d’interaction de couche \(TIP\). La collecte de données de TIP est prise en charge en utilisant l’instrumentation.  
  
-   Options d’échantillonnage, telles que la définition de l’événement d’échantillonnage et l’intervalle de temporisation, ou la collecte de données de compteurs de performances supplémentaires.  
  
##  <a name="BKMK_Profiling_from_the_command_line"></a> Profilage à partir de la ligne de commande  
 Pour collecter les données de profilage sur les appareils Windows 8 et Windows Server 2012, y compris les appareils qui n’ont pas d’installation de Visual Studio, vous pouvez utiliser deux outils de ligne de commande :  
  
|Nom de l’outil|Description|  
|--------------------|-----------------|  
|[VSPerf](../profiling/vsperf.md)|Collecte les données de profilage à partir des applications du Windows Store et collecte les données de profilage d’échantillon à partir des applications de bureau Windows 8 et des applications Windows Server 2012.|  
|[VSPerfCmd](../profiling/vsperfcmd.md)|Collecte les données de profilage d’instrumentation, d’accès concurrentiel et d’interaction de couche à partir d’applications qui s’exécutent sur le bureau Windows 8 ou Windows Server 2012. Collecte tous les types de données de profilage à partir des versions précédentes de Windows.|  
  
 Les deux outils sont installés avec Visual Studio pour être utilisés sur l’ordinateur local.  
  
 Pour profiler des applications sur les appareils dépourvus de Visual Studio, procédez de l’une des façons suivantes :  
  
-   Téléchargez les outils dans le cadre des Outils de contrôle à distance pour Visual Studio à partir du [site web MSDN](http://go.microsoft.com/fwlink/?LinkID=219549).  
  
-   Copiez et exécutez le programme d’installation des outils de profilage autonomes à partir de votre ordinateur Visual Studio. Les programmes d’installation se trouvent dans le dossier *VSInstallDir%* **\\Team Tools\\Performance Tools\\Setups**. Choisissez le programme d’installation correspondant au système d’exploitation \(x86\/x64\) de l’ordinateur distant.  
  
> [!NOTE]
>  Pour collecter les données de profilage TIP, vous devez installer le profileur autonome de votre ordinateur Visual Studio sur l’ordinateur distant.  
  
 Ces fonctionnalités et options de profilage ne sont pas prises en charge quand il s’agit de profiler des applications Windows 8 et Windows Server 2012 à partir de la ligne de commande :  
  
-   Collecte de données à partir d’applications web Windows 8 et Windows Server 2012 en utilisant le mode d’échantillonnage avec [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).  
  
-   Collecte des données d’échantillonnage à l’aide de VsPerfCmd.exe.  
  
-   Options d’échantillonnage, telles que la définition de l’événement d’échantillonnage et l’intervalle de temporisation, ou la collecte de données de compteurs de performances supplémentaires.  
  
##  <a name="BKMK_Collecting_tier_interaction__TIP__data"></a> Collecte des données d'interaction de couche \(TIP\)  
 Le profilage d’interaction de couche fournit des informations supplémentaires sur les temps d’exécution des fonctions d’applications multicouches qui communiquent avec des bases de données via les services ADO.NET. Les données sont collectées uniquement pour les appels de fonctions synchrones.  
  
 **Éditions Visual Studio**  
  
 Les données de profilage d’interaction de couche peuvent être collectées en utilisant [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] ou [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)]. Cependant, les données de profilage d’interaction de couche ne peuvent être affichées que dans [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] et [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
 **Windows 8 et Windows Server 2012**  
  
1.  Pour collecter des données d’interaction de couche à partir d’applications qui s’exécutent sur le bureau Windows 8 ou Windows Server 2012, vous devez utiliser la méthode d’instrumentation.  
  
2.  Vous ne pouvez pas collecter de données d’interaction de couche pour les applications du Windows Store.  
  
3.  Vous pouvez inclure des données d’interaction de couche dans toutes les méthodes de profilage sur les autres versions prises en charge de Windows.  
  
 **Assistant Performance et Explorateur de performances**  
  
 Vous devez ajouter l’option de collecte de données d’interaction de couche à une exécution du profilage à partir de l’Explorateur de performances. Vous devez aussi ajouter le projet, l’exécutable ou le site web au nœud cible de l’Explorateur de performances. Consultez [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md).  
  
 **Collecte de données TIP sur un ordinateur distant**  
  
 Pour collecter des données d’interaction de couche sur un ordinateur distant, vous devez copier le fichier **vs\_profiler\_***\<Plateforme\>***\_***\<Langue\>***.exe** du dossier *VSInstallDir %***\\Team Tools\\Performance Tools\\Setups** d’un ordinateur Visual Studio vers l’ordinateur distant et l’installer. Vous ne pouvez pas utiliser les outils de profilage contenus dans le package de téléchargement [Outils de contrôle à distance de Visual Studio](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
 Vous pouvez utiliser [VSPerfCmd](../profiling/vsperfcmd.md) ou [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) pour collecter les données de profilage.  
  
 **Rapports TIP**  
  
 Les données d’interaction de couche ne peuvent être affichées que dans l’IDE [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] ou [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]. Les rapports d’interaction de couche basés sur des fichiers procédant de [VSPerfReport](../profiling/vsperfreport.md) ne sont pas disponibles.  
  
## Voir aussi  
 [Utilisation des outils de profilage](../profiling/performance-explorer.md)   
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)