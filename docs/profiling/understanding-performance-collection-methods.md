---
title: "Fonctionnement des m&#233;thodes de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.wizard.methodpage"
helpviewer_keywords: 
  - "Outils de profilage, méthodes de profilage"
ms.assetid: ea4881fd-bd04-4875-9b7b-28490d6706f9
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Fonctionnement des m&#233;thodes de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les outils de profilage Visual Studio fournissent cinq méthodes que vous pouvez utiliser pour collecter les données de performance.  Cette rubrique décrit les différentes méthodes et suggère quelques scénarios dans lesquels la collecte de données avec une méthode particulière peut s'avérer appropriée.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans Windows 8 et Windows Server 2012 nécessitaient d'importantes modifications de la manière dont le profileur Visual Studio collecte des données sur ces plateformes.  Les applications Windows Store requièrent également de nouvelles techniques de collecte.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Échantillonnage](#sampling)|Collecte des données statistiques sur le travail effectué par une application.|  
|[Instrumentation](#instrumentation)|Collecte des informations détaillées de minutage sur chaque appel de fonction.|  
|[l'accès concurrentiel ;](#concurrency)|Collecte des informations détaillées sur les applications multithreads.|  
|[Mémoire .NET](#net_memory)|Collecte des informations détaillées sur l'allocation de mémoire .NET et le garbage collection.|  
|[Interaction de couche](#tier_interaction)|Collecte des informations sur les appels de fonction ADO.NET synchrones à une base de données SqlServer.<br /><br /> Les données de profilage d'interaction de couche peuvent être collectées à l'aide de [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], ou [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)].  Toutefois, les données de profilage d'interaction de couche peuvent être affichées uniquement dans [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] ou [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)].|  
  
 En utilisant certaines méthodes de profilage, vous pouvez également collecter des données supplémentaires, telles que des compteurs de performance logiciels et matériels.  Pour plus d'informations, consultez [Collecte de données de performance supplémentaires](../profiling/collecting-additional-performance-data.md).  
  
##  <a name="sampling"></a> Échantillonnage  
 La méthode de profilage par échantillonnage collecte des données statistiques sur le travail effectué par une application pendant une exécution de profilage.  La méthode d'échantillonnage est légère et a peu d'effet sur l'exécution des méthodes d'application.  
  
 L'échantillonnage est la méthode par défaut des outils de profilage Visual Studio.  Il est utile pour :  
  
-   Les explorations initiales de la performance de votre application.  
  
-   Examen des problèmes de performances qui impliquent l'utilisation du processeur \(UC\).  
  
 La méthode de profilage par échantillonnage interrompt le processeur de l'ordinateur à intervalles définis et collecte la pile des appels de fonction.  Les nombres d'exemples exclusifs sont incrémentés pour la fonction qui s'exécute et les nombres inclusifs sont incrémentés pour toutes les fonctions d'appel sur la pile des appels.  Les rapports d'échantillonnage présentent les totaux de ces nombres pour le module, la fonction, la ligne de code source et l'instruction profilés.  
  
 Par défaut, le profileur définit l'intervalle d'échantillonnage sur des cycles microprocesseurs.  Vous pouvez modifier le type d'intervalle pour choisir un autre compteur de performance d'UC et définir le nombre d'événements de compteur pour l'intervalle.  Vous pouvez également collecter des données de profilage d'interaction de couche \(TIP\) qui fournissent des informations sur les requêtes exécutées sur une base de données SQL Server via ADO.NET.  
  
 [Collecte de statistiques de performance à l’aide de l’échantillonnage](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
 [Fonctionnement des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md)  
  
 [Vues de données de la méthode d'échantillonnage](../profiling/profiler-sampling-method-data-views.md)  
  
##  <a name="instrumentation"></a> Instrumentation  
 La méthode de profilage par instrumentation collecte les informations de minutage détaillées pour les appels de fonction dans une application profilée.  Le profilage par instrumentation est utile pour :  
  
-   Examen des goulots d'étranglement d'entrée\/sortie tels que l'E\/S de disque.  
  
-   Examen détaillé d'un module ou ensemble de fonctions particulier.  
  
 La méthode d'instrumentation injecte le code dans un fichier binaire qui capture les informations de minutage pour chaque fonction du fichier instrumenté et chaque appel de fonction passé par ces fonctions.  L'instrumentation identifie également si une fonction fait appel au système d'exploitation pour des opérations telles que l'écriture dans un fichier.  Les rapports d'instrumentation utilisent quatre valeurs pour représenter le temps total passé dans une fonction ou une ligne de code source :  
  
-   Temps inclusif écoulé : temps total passé dans l'exécution de la fonction ou de la ligne source.  
  
-   Temps inclusif d'application : temps passé dans l'exécution de la fonction ou de la ligne source, à l'exception du temps passé dans les appels au système d'exploitation.  
  
-   Temps exclusif écoulé : temps passé dans l'exécution du code dans le corps de la fonction ou de la ligne de code source.  Le temps passé dans l'exécution des fonctions appelées par la fonction ou la ligne source est exclu.  
  
-   Temps exclusif d'application : temps passé dans l'exécution du code dans le corps de la fonction ou de la ligne de code source.  Le temps passé dans l'exécution des appels au système d'exploitation et le temps passé dans l'exécution des fonctions appelées par la fonction ou la ligne source sont exclus.  
  
 Vous pouvez également collecter à la fois les compteurs de performance d'UC et de logiciel à l'aide de la méthode d'instrumentation.  
  
 [Fonctionnement des valeurs de données d’instrumentation](../profiling/understanding-instrumentation-data-values.md)  
  
 [Collecte de données de temporisation détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)  
  
 [Vues de données de la méthode d'instrumentation](../profiling/instrumentation-method-data-views.md)  
  
##  <a name="concurrency"></a> l'accès concurrentiel ;  
 Le profilage d'accès concurrentiel collecte des informations sur les applications multithreads.  Le profilage de conflit de ressources collecte des informations détaillées de pile des appels chaque fois que des threads en concurrence sont forcés d'attendre l'accès à une ressource partagée.  La visualisation concurrentielle collecte également davantage d'informations générales sur l'interaction de votre application multithread avec elle\-même, le matériel, le système d'exploitation et d'autres processus sur l'ordinateur hôte :  
  
-   Les rapports de conflit de ressources affichent le nombre total de conflits et le temps total d'attente passé pour une ressource pour les modules, les fonctions, les lignes de code source et les instructions.  Les graphiques de chronologie affichent également les conflits tels qu'ils se sont produits.  
  
-   Le visualiseur concurrentiel affiche des informations graphiques que vous pouvez utiliser pour localiser les goulots d'étranglement au niveau des performances, la sous\-utilisation de l'UC, les conflits de threads, la migration de threads, les délais de synchronisation, les zones d'E\/S avec chevauchement et d'autres informations.  Lorsque cela s'avère possible, la sortie graphique est reliée à la pile des appels et aux données de code source.  Les données de visualisation concurrentielle peuvent être collectées uniquement pour la ligne de commande et les applications Windows.  
  
 [Fonctionnement des valeurs de données de conflit de ressources](../profiling/understanding-resource-contention-data-values.md)  
  
 [Collecte de données de concurrence de threads et de processus](../profiling/collecting-thread-and-process-concurrency-data.md)  
  
 [Vues de données de conflit de ressources](../profiling/resource-contention-data-views.md)  
  
 [Visualiseur concurrence](../profiling/concurrency-visualizer.md)  
  
##  <a name="net_memory"></a> Mémoire .NET  
 La méthode de profilage d'allocation de mémoire .NET interrompt le processeur de l'ordinateur à chaque allocation d'un objet .NET Framework dans une application profilée.  Lorsque les données de durée de vie de l'objet sont également collectées, le profileur interrompt le processeur après chaque garbage collection .NET Framework.  
  
 Le profileur collecte des informations sur le type, la taille et le nombre des objets créés dans une allocation ou détruits dans un garbage collection.  
  
-   Lorsqu'un événement d'allocation se produit, le profileur collecte des informations supplémentaires sur la pile des appels de fonction.  Les nombres d'allocations exclusifs sont incrémentés pour la fonction actuellement exécutée et les nombres inclusifs sont incrémentés pour toutes les fonctions d'appel sur la pile des appels. Les rapports .NET présentent les totaux de ces nombres pour les types, les modules, les fonctions, les lignes de code source et les instructions profilés.  
  
-   Lorsqu'un garbage collection se produit, le profileur collecte des données sur les objets détruits et des informations sur les objets de chaque génération de garbage collection.  À la fin de l'exécution du profilage, le profileur enregistre des données sur les objets qui n'ont pas été détruits explicitement.  Le rapport Durée de vie des objets affiche les totaux pour chaque type alloué dans l'exécution du profilage.  
  
 Les profils de mémoire .NET peuvent être utilisés en mode d'échantillonnage ou d'instrumentation.  Le mode que vous sélectionnez n'affecte pas les rapports Allocation et Durée de vie des objets qui sont uniques aux profils de mémoire .NET :  
  
-   Lorsque vous exécutez les profils de mémoire .NET en mode d'échantillonnage, le .NET du profileur utilise des événements d'allocation de mémoire comme intervalle et affiche le nombre d'objets alloués et le nombre total d'octets alloués comme valeurs inclusives et exclusives dans les rapports.  
  
-   Lorsque vous exécutez les profils de mémoire .NET en mode d'instrumentation, des informations détaillées de minutage sont collectées avec les valeurs d'allocation inclusives et exclusives.  
  
 [Fonctionnement de l’allocation de mémoire et des informations de durée de vie des objets](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)  
  
 [Collecte de données liées à l’allocation et à la durée de vie de la mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
 [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)  
  
##  <a name="tier_interaction"></a> Interaction de couche  
 Le profilage d'interaction de couche ajoute des informations à un fichier de données de profilage sur les appels [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] synchrones entre une page [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ou une autre application et une base de données [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].  Les données incluent le nombre d'appels et l'heure, ainsi que le nombre maximal et minimal d'appels.  Les données d'interaction de couche peuvent être ajoutées aux données de profilage collectées avec les méthodes d'échantillonnage, d'instrumentation, de mémoire .NET ou de concurrence.  
  
 ![Données de profilage d'interaction de couche](../profiling/media/tierinteraction_profilingtools.png "TierInteraction\_ProfilingTools")  
Données d'interaction de couche collectées par les outils de profilage  
  
 [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)  
  
 [Interaction de couche, vues](../profiling/tier-interaction-views.md)  
  
## Voir aussi  
 [Procédure : collecte des données de performances pour un site web](../profiling/how-to-collect-performance-data-for-a-web-site.md)   
 [Guide du débutant en profilage des performances](../profiling/beginners-guide-to-performance-profiling.md)