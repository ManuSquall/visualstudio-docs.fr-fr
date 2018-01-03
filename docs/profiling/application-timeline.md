---
title: "Analyser la consommation des ressources dans les applications XAML sous Visual Studio | Microsoft Docs"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 3109f33c24b3ff217f6e48c6458a4c6514b0b151
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>Analyser la consommation des ressources et l’activité des threads de l’interface utilisateur (XAML)
Utilisez le profileur **Chronologie de l'application** pour rechercher et corriger les problèmes de performances liés à l'interaction d'application dans les applications XAML. Cet outil vous aide à améliorer les performances des applications XAML en fournissant une vue détaillée de la consommation des ressources des applications. Vous pouvez analyser le temps passé par votre application à préparer les trames de l'interface utilisateur (mise en page et rendu), à traiter les demandes du réseau et des disques, et dans les scénarios comme le démarrage de l'application, le chargement des pages et le redimensionnement des fenêtres.  
  
 La **Chronologie de l’application** fait partie des outils que vous pouvez démarrer avec la commande **Déboguer -> Profileur de performances...**.  
  
 Cet outil remplace l'outil **Réactivité de l'interface utilisateur XAML** , qui faisait partie de l'ensemble d'outils de diagnostic pour Visual Studio 2013.  
  
 Vous pouvez utiliser cet outil sur les plateformes suivantes :  
  
1.  Applications universelles Windows (sur Windows 10)  
  
2.  Windows 8.1  
  
3.  Windows Phone 8.1 (Plateforme XAML commune)  
  
4.  Windows Presentation Foundation (.Net 4.0 et ultérieur)  
  
5.  Windows 7  
  
> [!NOTE]
>  Vous pouvez collecter et analyser les données d'utilisation de l'UC et les données de consommation d'énergie en même temps que les données de **Chronologie de l'application** . Consultez [Exécution des outils de profilage avec ou sans le débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md).
  
##  <a name="BKMK_Collect_Timeline_data_for_your_app"></a> Collecter les données de chronologie de l’application  
 Vous pouvez profiler la réactivité de votre application sur votre ordinateur local, sur votre appareil connecté, sur le simulateur ou les émulateurs Visual Studio, ou sur un appareil distant. Consultez [Exécution des outils de profilage avec ou sans le débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md).
  
> [!TIP]
>  Si possible, exécutez l'application directement sur l'appareil. Les performances de l'application observées sur le simulateur ou via une connexion Bureau à distance peuvent ne pas être identiques aux performances réelles sur l'appareil. D'autre part, la collecte des données à l'aide des outils distants Visual Studio n'affecte pas les données de performances.  
  
 Les étapes de base sont les suivantes :  
  
1.  Ouvrez votre application XAML.  
  
2.  Cliquez sur **Déboguer -> Profileur de performances...**. Vous devez voir une liste des outils de profilage dans la fenêtre .diagsession.  
  
3.  Sélectionnez **Chronologie de l'application** , puis cliquez sur **Démarrer** dans le bas de la fenêtre.  
  
    > [!NOTE]
    >  Il est possible qu'une fenêtre Contrôle de compte d'utilisateur apparaisse et vous demande l'autorisation d'exécuter VsEtwCollector.exe. Cliquez sur **Oui**.  
  
4.  Exécutez le scénario qui vous intéresse quant au profilage dans votre application pour collecter des données de performances.  
  
5.  Pour arrêter le profilage, revenez à la fenêtre .diagsession et cliquez sur **Arrêter** dans le haut de la fenêtre.  
  
     Visual Studio analyse les données collectées et affiche les résultats.  
  
     ![Rapport du profileur de chronologie](../profiling/media/timeline_base.png "TIMELINE_Base")  
  
##  <a name="BKMK_Analyze_Timeline_profiling_data"></a> Analyser les données de profilage de la chronologie  
 Après avoir collecté les données de profilage, vous pouvez utiliser ces étapes pour démarrer votre analyse :  
  
1.  Consultez les informations dans les graphiques **Utilisation de threads d'interface utilisateur** et **Débit visuel (i/s)** puis utilisez les barres de navigation de la chronologie pour sélectionner une plage horaire à analyser.  
  
2.  À l'aide des informations des graphiques **Utilisation des threads de l'interface utilisateur** ou **Débit visuel (i/s)** , examinez les détails de la vue **Détails de la chronologie** pour découvrir les causes possibles d'un manque apparent de réactivité.  
  
###  <a name="BKMK_Report_scenarios_categories_and_events"></a> Scénarios de rapport, catégories et événements  
 L'outil **Chronologie de l'application** affiche les données de la chronologie pour les scénarios, les catégories et les événements liés aux performances XAML.  
  
###  <a name="BKMK_Diagnostic_session_timeline"></a> Chronologie de session de diagnostic  
 ![Chronologie des performances et des diagnostics](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")  
  
 La règle située en haut de la page affiche la chronologie des informations profilées. Cette chronologie s'applique aux deux graphiques **Utilisation de threads d'interface utilisateur** et **Débit visuel** . Vous pouvez limiter la portée du rapport en faisant glisser les barres de navigation sur la chronologie pour sélectionner un segment de la chronologie.  
  
 La chronologie affiche également les marques utilisateur que vous avez insérées, et les événements de cycle de vie de l'activation de l'application.  
  
###  <a name="BKMK_UI_thread_utilization_graph"></a> Graphique d’utilisation du thread d’interface utilisateur  
 ![Graphique d’utilisation du processeur](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")  
  
 Le graphique **Utilisation des threads d'interface utilisateur (%)** est un graphique à barres qui affiche la quantité relative de temps passé dans une catégorie pendant un intervalle de collecte.  
  
###  <a name="BKMK_Visual_throughput_FPS_graph"></a> Graphique du débit visuel (images par seconde)  
 ![Graphique du débit visuel](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")  
  
 Le diagramme linéaire **Débit visuel (i/s)** montre les images par seconde (FPS) sur l'interface utilisateur et le thread de composition pour l'application.  
  
###  <a name="BKMK_Timeline_details_"></a> Détails de la chronologie  
 C'est dans la vue Détails que vous passerez le plus de temps à analyser le rapport. Il montre une vue détaillée de l’utilisation de l’UC par votre application, en fonction de la catégorie du sous-système du framework d’interface utilisateur ou du composant système qui a consommé l'UC.  
  
 Les événements suivants sont pris en charge :  
  
|||  
|-|-|  
|**Analyse**|Temps passé à l'analyse de fichiers XAML et à la création d'objets.<br /><br /> Le développement d'un nœud **Analyse** dans **Détails de la chronologie** affiche la chaîne de dépendance de tous les fichiers XAML qui ont été analysés comme résultat de l'événement racine. Cela vous permettra d'identifier l'analyse de fichiers inutiles et la création d'objets dans les scénarios critiques de performances, et de les optimiser.|  
|**Disposition**|Dans les grandes applications, des milliers d'éléments peuvent s'afficher en même temps sur l'écran. Ceci peut entraîner un faible débit des trames d'interface utilisateur et en conséquence, une réactivité faible de l'application. L’événement Layout détermine avec précision le coût de la disposition de chaque élément (c’est-à-dire le temps passé dans les fonctions Arrange, Measure, ApplyTemplate et ArrangeOverride) et génère les arborescences des éléments visuels qui ont participé à une passe de disposition. Vous pouvez utiliser cette visualisation pour déterminer laquelle de vos arborescences logiques doit être élaguée ou pour évaluer d'autres mécanismes de report pour optimiser votre passe de disposition.|  
|**Afficher**|Temps passé à dessiner les éléments XAML à l'écran.|  
|**E/S**|Durée de récupération de données à partir du disque local ou à partir des ressources réseau qui sont accessibles par le biais de l’ [API Microsoft Windows Internet (WinINet)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa385331.aspx).|  
|**Code d'application**|Indique le temps passé à l'exécution du code de l'application (utilisateur) qui n'est pas lié à l'analyse ou à la disposition.|  
|**Autres Xaml**|Temps passé à exécuter le code du runtime XAML.|  
  
> [!TIP]
>  Choisissez l'outil **Utilisation de l'UC** ainsi que l'outil **Chronologie de l'application** quand vous démarrez le profilage pour afficher les méthodes de l'application qui s'exécutent sur le thread d'interface utilisateur. Le déplacement d'un code d'application de longue durée vers un thread d'arrière-plan peut améliorer la réactivité de l'interface utilisateur.  
  
####  <a name="BKMK_Customizing_Timeline_details_"></a> Personnalisation des détails de la chronologie  
 Utilisez la barre à outils **Détails de la chronologie** pour trier, filtrer et spécifier les annotations des entrées de la vue **Détails de la chronologie** .  
  
|||  
|-|-|  
|**Trier par**|Triez par heure de début ou sur la longueur des événements.|  
|![Regrouper les événements par frame](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|Ajoute ou supprime une catégorie **Image** qui regroupe les événements par image.|  
|![Filtrer la liste des détails de chronologie](../profiling/media/timeline_filter.png "TIMELINE_Filter")|Filtre la liste par catégories sélectionnées et longueur des événements.|  
|![Personnaliser les informations de détails de chronologie](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|Permet de spécifier des annotations sur les événements.|  
  
## <a name="see-also"></a>Voir aussi  
 [Blog de l’équipe WPF : New UI Performance Analysis Tool for WPF Applications](http://blogs.msdn.com/b/wpf/archive/2015/01/16/new-ui-performance-analysis-tool-for-wpf-applications.aspx)  
 [Bonnes pratiques pour les performances des applications UWP en C++, C# et Visual Basic](http://msdn.microsoft.com/en-us/567bcefa-5da5-4e42-a4b8-1358c71adfa2)   
 [Optimisation des performances des applications WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)  
 [Profilage dans Visual Studio](../profiling/index.md)  
 [Visite guidée des fonctionnalités de profilage](../profiling/profiling-feature-tour.md)
