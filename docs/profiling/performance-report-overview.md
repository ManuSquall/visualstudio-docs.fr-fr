---
title: Vue d’ensemble du rapport Performances | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 455c05ae0d8645040d3f9eac68d20f57138df5cb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830767"
---
# <a name="performance-report-overview"></a>Vue d’ensemble du rapport Performances
Vous pouvez afficher les données de profilage d’une session de performance dans la fenêtre **Rapport de performances** de l’environnement de développement intégré (IDE) de Visual Studio Team System Development Edition. Les données de profilage sont enregistrées dans des fichiers .vsp et .vsps. Grâce aux fenêtres de vue Rapport, vous pouvez afficher et analyser les problèmes de performances d’une application.  
  
> [!CAUTION]
>  Un fichier de données de profilage contient des informations sensibles telles que le nom de l’ordinateur, la version du système d’exploitation, les chemins des fichiers, les informations sur la mémoire et d’autres informations relatives à la configuration de l’ordinateur. Vous devez maintenir un contrôle strict sur la distribution des données, aussi bien au format natif .*vsp* qu’en cas d’exportation vers un fichier .*csv* ou .*xml*.  
>   
>  Si les données de suivi d’événements sont collectées dans le cadre de la session de performance, des informations supplémentaires peuvent s’afficher dans le fichier journal de suivi d’événements (.*etl*). Ces informations incluent votre nom de domaine et d’utilisateur ; par conséquent, vous devez maintenir un contrôle strict sur la distribution du fichier journal.  
  
## <a name="performance-report-window"></a>Fenêtre Rapport de performances  
 La fenêtre Rapport de performances est une fenêtre Outil permettant d’afficher, de gérer et de filtrer les données de performance et qui inclut un contrôle de requête personnalisable.  
  
 La barre d’outils principale de la fenêtre Rapport de performances vous permet d’accéder à chaque vue. Cliquez sur la flèche située en regard de la liste **Affichage actuel** pour afficher et sélectionner les différentes vues disponibles.  
  
 La fenêtre Rapport de performances fournit les vues de données suivantes :  
  
### <a name="summary-view"></a>Vue Résumé  
 Par défaut, les données de profilage s’affichent dans la vue Résumé. Cette vue constitue un point de départ pour votre examen de problèmes de performances. À partir de chaque ligne de la vue Résumé, vous pouvez passer à des vues plus détaillées en cliquant avec le bouton droit sur le nom de la fonction ou du module. Pour plus d’informations, consultez [Résumé, vue](../profiling/summary-view.md).  
  
### <a name="callercallee-view"></a>Vue Appelant/Appelé  
 La vue Appelant/Appelé affiche une arborescence des appels pour une fonction spécifique. Cette vue est composée de trois parties :  
  
- La fonction cible figure au milieu de la vue.  
  
- Les fonctions qui ont appelé la fonction (appelants) sont affichées au-dessus de la fonction cible.  
  
- Les fonctions qui sont appelées par la fonction cible (appelés) sont affichées sous la cible.  
  
  Vous pouvez sélectionner une fonction différente en double-cliquant sur n’importe quelle fonction de la liste des appelés ou des appelants. Pour plus d’informations, consultez [Vue Appelant/Appelé](../profiling/caller-callee-view.md).  
  
### <a name="call-tree-view"></a>Vue Arborescence des appels  
 La vue Arborescence des appels affiche les chemins d’exécution de la fonction empruntés dans l’application profilée. La racine de l’arborescence correspond au point d’entrée de l’application ou du composant. Chaque nœud de fonction répertorie toutes les fonctions appelées et les données de performance liées à ces appels de fonction.  
  
 La vue Arborescence des appels peut également être développée et mettre en surbrillance le chemin d’exécution d’une fonction qui a exigé le plus de temps ou qui a fait l’objet du plus grand nombre d’échantillonnages. Pour afficher le chemin le plus actif, cliquez avec le bouton droit sur la fonction, puis cliquez sur **Développer le chemin réactif**. Pour plus d’informations, consultez [Arborescence des appels, vue](../profiling/call-tree-view.md).  
  
### <a name="process-view"></a>Vue Processus  
 La vue Processus affiche les données de performance pour chaque processus et thread profilés. Pour plus d’informations, consultez [Processus, vue](../profiling/process-view.md).  
  
### <a name="modules-view"></a>Vue Modules  
 La vue Modules répertorie les modules présents dans le projet et affiche les données de profilage de chaque module. Développez ou réduisez le nom d’un module pour afficher les données de profilage de fonction. Une fois les données collectées à l’aide de l’échantillonnage, les données de profilage de la ligne de code source et du pointeur d’instruction sont également disponibles. Pour plus d’informations, consultez [Modules, vue](../profiling/modules-view.md).  
  
### <a name="functions-view"></a>Vue Fonctions  
 La vue Fonctions répertorie les fonctions appelées lors du profilage. Pour plus d’informations, consultez [Fonctions, vue](../profiling/functions-view.md).  
  
### <a name="line-view"></a>Vue Lignes  
 La vue lignes permet d’afficher les lignes de code source spécifiques exécutées au cours du profilage d’échantillonnage. Pour plus d’informations, consultez [Lignes, vue](../profiling/lines-view.md).  
  
### <a name="instruction-pointer-ip-view"></a>Vue Pointeurs d’instruction (IP)  
 La vue Pointeurs d’instruction vous permet de consulter les instructions spécifiques qui ont été exécutées pendant le profilage d’échantillonnage. Pour plus d’informations, consultez [Pointeurs d’instruction (IP), vue](../profiling/instruction-pointers-ips-view.md).  
  
### <a name="allocation-view"></a>Vue Allocations  
 La vue Allocations est disponible si l’option **Collecter les informations d’allocation d’objets .NET** a été sélectionnée dans la page **Général** de la boîte de dialogue de propriétés **Session de performance**. Consultez [Vue d’ensemble des sessions de performances](../profiling/performance-session-overview.md). La vue Allocations répertorie les objets .NET alloués par l’application ou le composant. Quand vous développez une ligne d’objet, une arborescence des appels s’affiche. Elle indique les chemins d’exécution qui ont entraîné la création de l’objet. Cette arborescence affiche également des informations sur le nombre d’allocations inclusives et exclusives pour chaque fonction. La vue Allocations peut également être développée pour mettre en surbrillance le chemin d’exécution d’une fonction qui a alloué le plus grand nombre d’objets. Pour afficher le chemin le plus actif, cliquez avec le bouton droit sur la fonction, puis cliquez sur **Développer le chemin réactif**. Pour plus d’informations, consultez [Collecter des données liées à la durée de vie des objets et à l’allocation de mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) et [Allocations, vue](../profiling/dotnet-memory-allocations-view.md).  
  
### <a name="objects-lifetime-view"></a>Vue Durée de vie des objets  
 La vue Durée de vie des objets est disponible si les options **Collecter les informations d’allocation d’objets .NET** et **Collecter aussi les informations de durée de vie des objets .NET** ont été sélectionnées dans la page **Général** de la boîte de dialogue de propriétés **Session de performance**.  
  
 La vue Durée de vie des objets affiche le nombre total d’instances de chaque type et le nombre d’objets collectés dans chaque génération de garbage collection. Pour plus d’informations, consultez [Durée de vie des objets, vue](../profiling/object-lifetime-view.md).  
  
## <a name="customizable-filter-control"></a>Contrôle de filtre personnalisable  
 Le contrôle de filtre personnalisable comporte les options suivantes :  
  
-   **Importer le filtre** : récupère une requête personnalisée précédemment enregistrée.  
  
-   **Exporter le filtre** : enregistre la requête personnalisée dans l’emplacement spécifié.  
  
-   **Exécuter la requête** : exécute la requête comme affiché dans le contrôle de requête personnalisée.  
  
-   **Arrêter la requête** : interrompt l’exécution d’une requête. Ce bouton n’est pas disponible si aucune requête n’est en cours d’exécution.  
  
-   **Afficher la requête** : affiche/masque le contrôle de requête personnalisée.  
  
-   **Enregistrer l’analyse** : enregistre le rapport avec son analyse actuelle dans un fichier .vsps.  
  
-   **Exporter** : enregistre le rapport actuel dans un fichier au format .CVS ou .XML, avec des options pour enregistrer les différentes vues.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser les données des outils d’analyse des performances](../profiling/analyzing-performance-tools-data.md)   
 [Vues du rapport des performances](../profiling/performance-report-views.md)