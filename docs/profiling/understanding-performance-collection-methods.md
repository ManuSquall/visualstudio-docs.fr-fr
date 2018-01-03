---
title: "Présentation des méthodes de collecte des performances | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.wizard.methodpage
helpviewer_keywords: Profiling Tools, profiling methods
ms.assetid: ea4881fd-bd04-4875-9b7b-28490d6706f9
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a126ec0329695455013ca8625a8aeb774cf2ad36
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-performance-collection-methods"></a>Présentation des méthodes de collecte des performances
Les outils de profilage Visual Studio fournissent cinq méthodes que vous pouvez utiliser pour collecter des données de performances. Cette rubrique décrit les différentes méthodes et suggère quelques scénarios dans lesquels la collecte des données avec une méthode particulière peut être appropriée.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Méthode|Description|  
|------------|-----------------|  
|[Échantillonnage](#sampling)|Collecte des données statistiques sur le travail effectué par une application.|  
|[Instrumentation](#instrumentation)|Collecte des informations de minutage détaillées sur chaque appel de fonction.|  
|[Concurrence](#concurrency)|Collecte des informations détaillées sur les applications multithreads.|  
|[Mémoire .NET](#net_memory)|Collecte des informations détaillées sur l’allocation et la garbage collection de la mémoire .NET.|  
|[Interaction de couche](#tier_interaction)|Collecte des informations sur les appels de fonction ADO.NET synchrones à une base de données SQL Server.<br /><br /> Les données de profilage d’interaction de couche peuvent être collectées en utilisant [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] ou [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)]. Cependant, les données de profilage d’interaction de couche ne peuvent être affichées que dans [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] ou [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)].|  
  
 À l’aide de certaines méthodes de profilage, vous pouvez également collecter des données supplémentaires, comme les compteurs de performances matérielles et logicielles. Pour plus d’informations, consultez [Collecte de données de performances supplémentaires](../profiling/collecting-additional-performance-data.md).  
  
##  <a name="sampling"></a> Échantillonnage  
 La méthode de profilage par échantillonnage collecte des données statistiques sur le travail effectué par une application pendant l’exécution d’un profilage. La méthode d’échantillonnage est légère et a peu d’effet sur l’exécution des méthodes de l’application.  
  
 L’échantillonnage est la méthode par défaut pour les outils de profilage de Visual Studio. Il est utile dans les cas suivants :  
  
-   Explorations initiales des performances de votre application.  
  
-   Examen des problèmes de performances qui impliquent l’utilisation du processeur (UC).  
  
 La méthode de profilage par échantillonnage interrompt le processeur de l’ordinateur à des intervalles définis et collecte la pile des appels des fonctions. Les totaux des échantillons exclusifs sont incrémentés pour la fonction en cours d’exécution et les totaux inclusifs sont incrémentés pour toutes les fonctions appelantes sur la pile des appels. Les rapports d’échantillonnage présentent les totaux de ces nombres pour le module, la fonction, la ligne de code source et l’instruction qui font l’objet du profilage.  
  
 Par défaut, le profileur définit l’intervalle d’échantillonnage sur la base des cycles de l’UC. Vous pouvez modifier le type d’intervalle pour un autre compteur de performances du processeur, et vous pouvez définir le nombre d’événements du compteur pour l’intervalle. Vous pouvez également collecter des données de profilage d’interaction de couche qui fournissent des informations sur les requêtes effectuées sur une base de données SQL Server via ADO.NET.  
  
 [Collecte de statistiques de performances à l’aide de l’échantillonnage](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
 [Présentation des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md)  
  
 [Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)  
  
##  <a name="instrumentation"></a> Instrumentation  
 La méthode de profilage par instrumentation collecte le minutage détaillé pour les appels de fonctions dans une application profilée. Le profilage par instrumentation est utile pour les cas suivants :  
  
-   Examen des goulots d’étranglement d’entrée/sortie, comme les E/S de disque.  
  
-   Examen détaillé d’un module ou d’un ensemble de fonctions particulier.  
  
 La méthode d’instrumentation injecte du code dans un fichier binaire, qui capture les informations de minutage pour chaque fonction du fichier instrumenté et pour chaque appel de fonction qui est fait à ces fonctions. L’instrumentation détecte également les appels d’une fonction au système d’exploitation pour des opérations comme l’écriture dans un fichier. Les rapports d’instrumentation utilisent quatre valeurs pour représenter le temps total passé dans une fonction ou une ligne de code source :  
  
-   Temps inclusif écoulé : temps total passé dans l’exécution de la fonction ou de la ligne source.  
  
-   Temps inclusif d’application : temps passé à l’exécution de la fonction ou de la ligne source, mais à l’exclusion du temps passé dans les appels au système d’exploitation.  
  
-   Temps exclusif écoulé : temps passé dans l’exécution du code dans le corps de la fonction ou de la ligne de code source. Le temps passé à l’exécution des fonctions appelées par la fonction ou par la ligne source est exclu.  
  
-   Temps exclusif d’application : temps passé dans l’exécution du code dans le corps de la fonction ou de la ligne de code source. Le temps passé à l’exécution des appels au système d’exploitation et le temps passé à l’exécution des fonctions appelées par la fonction ou la ligne source sont exclus.  
  
 Vous pouvez également collecter des compteurs de performances de l’UC et des logiciels à l’aide de la méthode d’instrumentation.  
  
 [Présentation des valeurs de données d’instrumentation](../profiling/understanding-instrumentation-data-values.md)  
  
 [Collecte de données de temporisation détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)  
  
 [Vues de données de la méthode d’instrumentation](../profiling/instrumentation-method-data-views.md)  
  
##  <a name="concurrency"></a> Accès concurrentiel  
 Le profilage d’accès concurrentiel collecte des informations sur les applications multithreads. Le profilage de conflit de ressources collecte les informations détaillées de la pile des appels chaque fois que des threads en concurrence sont forcés d’attendre pour accéder à une ressource partagée. La visualisation concurrentielle collecte également des informations plus générales sur la façon dont votre application multithread interagit avec elle-même, avec le matériel, avec le système d’exploitation et avec d’autres processus sur l’ordinateur hôte :  
  
-   Les rapports de conflit de ressources affichent le nombre total de conflits et le temps total passé en attente d’une ressource pour les modules, les fonctions, les lignes de code source et les instructions où l’attente s’est produite. Les graphiques chronologiques affichent également les conflits au fil de leur survenance.  
  
-   Le visualiseur concurrentiel affiche des informations graphiques que vous pouvez utiliser pour localiser les goulots d’étranglement au niveau des performances, la sous-utilisation de l’UC, les conflits de threads, la migration de threads, les délais de synchronisation, les zones d’E/S avec chevauchement et d’autres informations. Quand c’est possible, la sortie graphique est en lien avec les données de la pile des appels et du code source. Les données de visualisation concurrentielle peuvent être collectées uniquement pour les applications de ligne de commande et les applications Windows.  
  
 [Fonctionnement des valeurs des données de conflit de ressources](../profiling/understanding-resource-contention-data-values.md)  
  
 [Collecte de données concurrentielles de threads et de processus](../profiling/collecting-thread-and-process-concurrency-data.md)  
  
 [Vues de données de conflit de ressources](../profiling/resource-contention-data-views.md)  
  
 [Visualiseur concurrentiel](../profiling/concurrency-visualizer.md)  
  
##  <a name="net_memory"></a> Mémoire .NET  
 La méthode de profilage d’allocation de la mémoire .NET interrompt le processeur de l’ordinateur à chaque allocation d’un objet du .NET Framework dans une application profilée. Quand les données de durée de vie des objets sont également collectées, le profileur interrompt le processeur après chaque garbage collection du .NET Framework.  
  
 Le profileur collecte des informations sur le type, la taille et le nombre d’objets qui ont été créés dans une allocation ou détruits dans une garbage collection.  
  
-   Quand un événement d’allocation se produit, le profileur collecte des informations supplémentaires sur la pile d’appel des fonctions. Les totaux des allocations exclusives sont incrémentés pour la fonction en cours d’exécution et les totaux inclusifs sont incrémentés pour toutes les fonctions appelantes sur la pile des appels. Les rapports .NET présentent les totaux de ces nombres pour les types, les modules, les fonctions, les lignes de code source et les instructions qui font l’objet du profilage.  
  
-   Quand une garbage collection se produit, le profileur collecte des données sur les objets détruits et des informations sur les objets dans chaque génération de garbage collection. À la fin de l’exécution du profilage, le profileur enregistre des données sur les objets qui n’ont pas été explicitement détruits. Le rapport de durée de vie des objets affiche les totaux pour chaque type qui a été alloué dans l’exécution du profilage.  
  
 Le profilage de mémoire .NET peut être utilisé en mode d’échantillonnage ou d’instrumentation. Le mode que vous sélectionnez n’affecte pas les rapports d’allocation et de durée de vie des objets qui sont spécifiques au profilage de mémoire .NET :  
  
-   Quand vous exécutez un profilage de mémoire .NET en mode d’échantillonnage, le profileur .NET utilise les événements d’allocation de mémoire comme intervalle, et il affiche le nombre d’objets alloués et le nombre total d’octets alloués comme valeurs inclusives et exclusives dans les rapports.  
  
-   Quand vous exécutez le profilage de mémoire .NET en mode d’instrumentation, les informations détaillées de minutage sont collectées, ainsi que les valeurs d’allocation inclusives et exclusives.  
  
 [Fonctionnement de l’allocation de mémoire et des informations de durée de vie des objets](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)  
  
 [Collecte de données liées à l’allocation et à la durée de vie de la mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
 [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)  
  
##  <a name="tier_interaction"></a> Interaction de couche  
 Le profilage d’interaction de couche ajoute des informations à un fichier de données de profilage sur les appels [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] synchrones entre une page [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ou une autre application et une base de données [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. Les données incluent le nombre et la durée des appels, ainsi que la durée maximale et minimale. Les données d’interaction de couche peuvent être ajoutées aux données de profilage collectées avec les méthodes d’échantillonnage, d’instrumentation, de mémoire .NET ou d’accès concurrentiel.  
  
 ![Données de profilage d’interaction de couche](../profiling/media/tierinteraction_profilingtools.png "TierInteraction_ProfilingTools")  
Données d’interaction de couche collectées par les outils de profilage  
  
 [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)  
  
 [Vues Interactions de couche](../profiling/tier-interaction-views.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour collecter des données de performances pour un site web](../profiling/how-to-collect-performance-data-for-a-web-site.md)   
 [Guide du débutant en profilage des performances](../profiling/beginners-guide-to-performance-profiling.md)