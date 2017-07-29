---
title: "Analyser l’utilisation de l’UC dans Visual Studio | Microsoft Docs"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 795bf9746c4ae48ac04141a05ba56462ecb90482
ms.openlocfilehash: 74e69f0d5d04192eb801f5e56e1a4ee6ca2cc57a
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

---
# <a name="analyze-cpu-usage"></a>Analyser l'utilisation de l'UC
Lorsque vous devez étudier les problèmes de performances de votre application, un bon point de départ consiste à comprendre son utilisation du processeur. L’outil **Utilisation du processeur** vous montre où le processeur exécute du code Visual C++, Visual C#/Visual Basic et JavaScript. À compter de Visual Studio 2015 Update 1, vous pouvez afficher une répartition par fonction de l’utilisation du processeur sans quitter le débogueur. Vous pouvez activer et désactiver le profilage du processeur pendant le débogage, et afficher les résultats quand l’exécution est arrêtée, par exemple à un point d’arrêt.  
  
Vous disposez de plusieurs options pour exécuter et gérer votre session de diagnostic. Par exemple, vous pouvez exécuter l’outil **Utilisation du processeur** sur les ordinateurs locaux ou distants, ou bien dans un simulateur ou un émulateur. Vous pouvez analyser les performances d'un projet ouvert dans Visual Studio, attaché à une application en cours d'exécution, ou démarrer une application installée à partir du Windows Store. Pour plus d’informations, consultez [Exécution des outils de profilage avec ou sans débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Pour obtenir une procédure pas à pas qui analyse les performances d’une application du Windows Store, consultez [Analyser l’utilisation de l’UC dans les applications du Windows Store](analyze-cpu-usage-in-a-windows-universal-app.md). 

Nous vous montrons ici comment collecter et analyser l’utilisation de l’UC avec les versions finales. Pour analyser l’utilisation de l’UC pendant le débogage, consultez [Guide du débutant en profilage des performances](../profiling/beginners-guide-to-performance-profiling.md). 
  
##  <a name="BKMK_Collect_CPU_usage_data"></a> Collecter les données d’utilisation de l’UC  
  
1.  Dans Visual Studio, définissez la configuration de solution sur **Version finale** et choisissez la cible de déploiement.  
  
     ![Sélectionner la version et l’ordinateur local](../profiling/media/cpuuse_selectreleaselocalmachine.png "CPUUSE_SelectReleaseLocalMachine")  
  
    -   L'exécution de l'application en mode **Version finale** vous offre une meilleure vue des performances réelles de votre application.  
  
    -   L'exécution de l'application sur l'ordinateur local réplique au mieux l'exécution de l'application installée.  
  
    -   Si vous collectez les données à partir d'un appareil distant, exécutez l'application directement sur l'appareil et non par une connexion Bureau à distance.  
  
    -   Pour les applications Windows Phone, la collecte des données directement à partir de l' **Appareil** fournit les données les plus précises.  
  
2.  Dans le menu **Déboguer** , choisissez **Profileur de performances**.  
  
3.  Choisissez **Utilisation de l'UC** , puis **Démarrer**.  
  
     ![Cliquer sur Utilisation du processeur](../profiling/media/cpuuse_lib_choosecpuusage.png "CPUUSE_LIB_ChooseCpuUsage")  
  
4.  Lorsque l'application démarre, cliquez sur **Obtenir le nombre maximal**. Attendez environ une seconde après que la sortie s'est affichée, puis choisissez **Obtenir le nombre maximal asynchrone**. L'attente entre les clics de bouton permet plus facilement d'isoler les routines de clic de bouton dans le rapport de diagnostic.  
  
5.  Quand apparaît la deuxième ligne de sortie, choisissez **Arrêter la collecte** dans le hub Performances et diagnostics.  
  
 ![Arrêter la collecte des données CpuUsage](../profiling/media/cpu_use_wt_stopcollection.png "CPU_USE_WT_StopCollection")  
  
 L'outil Utilisation de l'UC analyse les données et affiche le rapport.  
  
 ![Rapport CpuUsage](../profiling/media/cpu_use_wt_report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a>Analyser le rapport d'utilisation de l'UC  
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> Arborescence des appels d'utilisation du processeur  
 Pour commencer la présentation des informations sur l'arborescence des appels, sélectionnez de nouveau le segment `GetMaxNumberButton_Click` et consultez les détails d'arborescence des appels.  
  
####  <a name="BKMK_Call_tree_structure"></a> Structure de l’arborescence des appels  
 ![Arborescence des appels GetMaxNumberButton&#95;Click](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![Étape 1](../profiling/media/procguid_1.png "ProcGuid_1")|Le nœud de premier niveau des arborescences d'appels de l'outil Utilisation de l'UC est un pseudo-nœud|  
|![Étape 2](../profiling/media/procguid_2.png "ProcGuid_2")|Dans la plupart des applications, quand l'option **Afficher le code externe** est désactivée, le nœud de deuxième niveau est un nœud **[Code externe]** contenant le code système et framework qui démarre et arrête l'application, dessine l'interface utilisateur, contrôle la planification des threads et fournit d'autres services de niveau inférieur à l'application.|  
|![Étape 3](../profiling/media/procguid_3.png "ProcGuid_3")|Les enfants du nœud de deuxième niveau sont les méthodes en code utilisateur et des routines asynchrones appelées ou créées par le code système et framework de deuxième niveau.|  
|![Étape 4](../profiling/media/procguid_4.png "ProcGuid_4")|Les nœuds enfants d'une méthode contiennent des données seulement pour les appels de la méthode parente. Lorsque l'option **Afficher le Code externe** est désactivée, les méthodes d'application peuvent également contenir un nœud **[Code externe]** .|  
  
####  <a name="BKMK_External_Code"></a> Code externe  
 Le code externe correspond aux fonctions des composants système et infrastructure exécutés par le code que vous écrivez. Le code externe inclut les fonctions qui démarrent et arrêtent l'application, dessinent l'interface utilisateur, contrôlent les threads et fournissent d'autres services de bas niveau à l'application. Dans la plupart des cas, vous ne serez pas intéressé par le code externe ; par conséquent, l’arborescence des appels de l’utilisation du processeur regroupe les fonctions externes d’une méthode utilisateur en un seul nœud **[Code externe]** .  
  
 Quand vous voulez afficher les chemins d'appel du code externe, choisissez **Afficher le code externe** dans la liste **Filtrer la vue** , puis **Appliquer**.  
  
 ![Choisir Filtrer l’affichage, puis Afficher le code externe](../profiling/media/cpu_use_wt_filterview.png "CPU_USE_WT_FilterView")  
  
 N'oubliez pas que de nombreuses chaînes d'appel en code externe sont profondément imbriquées, la largeur de la colonne Nom de fonction ne peut pas dépasser la largeur d'affichage de presque tous les moniteurs d'ordinateur, sauf les plus larges. Si tel est le cas, les noms de fonction sont affichés sous forme de **[…]** :  
  
 ![Code externe imbriqué dans l’arborescence des appels](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Utilisez la zone de recherche pour trouver le nœud que vous cherchez, puis utilisez la barre de défilement horizontal pour afficher les données dans la vue :  
  
 ![Rechercher du code externe imbriqué](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
###  <a name="BKMK_Call_tree_data_columns"></a> Colonnes des données de l’arborescence des appels  
  
|||  
|-|-|  
|**Processeur total (%)**|![Équation de données total (%)](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Pourcentage de l'activité du processeur de l'application dans la plage de temps sélectionnée qui a été utilisé par les appels de la fonction et les fonctions appelées par la fonction. Notez que cette information est différente du graphique chronologique **Utilisation du processeur** qui compare l'activité totale de l'application dans une plage de temps à la capacité totale disponible de l'UC.|  
|**Processeur auto (%)**|![Équation auto (%)](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Pourcentage de l'activité du processeur de l'application dans la plage de temps sélectionnée qui a été utilisé par les appels de la fonction, à l'exclusion de l'activité des fonctions appelées par la fonction.|  
|**Total processeur (ms)**|Nombre de millisecondes utilisées par les appels à la fonction dans la plage de temps sélectionnée et les fonctions appelées par la fonction.|  
|**Processeur auto (ms)**|Nombre de millisecondes utilisées par les appels à la fonction dans la plage de temps sélectionnée et les fonctions appelées par la fonction.|  
|**Module**|Nom du module contenant la fonction, ou le nombre de modules contenant les fonctions dans un nœud [Code externe].|  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Fonctions asynchrones de l'arborescence des appels de l'utilisation du processeur  
 Quand le compilateur rencontre une méthode asynchrone, il crée une classe masquée pour contrôler l’exécution de la méthode. Conceptuellement, la classe est une machine à états qui inclut la liste des fonctions générées par le compilateur qui appellent les opérations de la méthode d'origine en mode asynchrone, ainsi que les rappels, le planificateur et les itérateurs requis. Quand la méthode d’origine est appelée par une méthode parente, le runtime supprime la méthode du contexte d’exécution du parent et exécute les méthodes de la classe masquée dans le contexte du code système et du framework qui contrôle l’exécution de l’application. Les méthodes asynchrones sont souvent, mais pas toujours, exécutées sur un ou plusieurs threads différents. Ce code est affiché dans l'arborescence des appels de l'utilisation du processeur en tant qu'enfants du nœud **[Code externe]** situé immédiatement sous le nœud supérieur de l'arborescence.  
  
 Pour le voir dans notre exemple, resélectionnez le segment `GetMaxNumberAsyncButton_Click` dans la chronologie.  
  
 ![Sélection du rapport GetMaxNumberAsyncButton&#95;Click](../profiling/media/cpu_use_wt_getmaxnumberasync_selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Les deux premiers nœuds sous **[Code externe]** sont les méthodes générées par le compilateur de la classe de la machine d'état. Le troisième nœud est l'appel de la méthode d'origine. En développant les méthodes générées, vous obtenez un aperçu de ce qui se passe.  
  
 ![Arborescence des appels GetMaxNumberAsyncButton&#95;Click développée](../profiling/media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
-   `MainPage::GetMaxNumberAsyncButton_Click` se contente de gérer la liste des valeurs de la tâche, de calculer le nombre maximal de résultats et d'affiche la sortie.  
  
-   `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` affiche l'activité requise pour planifier et lancer les 48 tâches qui encapsulent l'appel à `GetNumberAsync`.  
  
-   `MainPage::<GetNumberAsync>b__b` affiche l'activité des tâches qui appellent `GetNumber`.
