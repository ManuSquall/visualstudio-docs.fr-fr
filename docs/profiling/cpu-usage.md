---
title: Analyser l’utilisation de l’UC | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2018
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbbad30fca5dd3ffbaa09c270f6a0b0400d9ea22
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640790"
---
# <a name="analyze-cpu-usage"></a>Analyser l’utilisation de l’UC

Une bonne façon de commencer l’investigation des problèmes de performances dans votre application consiste à comprendre son utilisation de l’UC. L’outil de performances **Utilisation de l’UC** montre le temps et le pourcentage de l’UC consacré à l’exécution du code dans les applications C++, C#/Visual Basic et JavaScript.

Vous pouvez exécuter l’outil **Utilisation de l’UC** sur un projet Visual Studio ouvert ou sur une application du Microsoft Store installée, ou bien l’attacher à une application ou un processus en cours d’exécution. Vous pouvez exécuter l’outil sur des ordinateurs locaux ou distants, ou sur un simulateur ou un émulateur. Pour plus d’informations, consultez [Exécution des outils de profilage avec ou sans débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Vous pouvez exécuter l’outil **Utilisation de l’UC** avec ou sans débogage. Dans le débogueur, vous pouvez activer et désactiver le profilage de l’UC, et afficher une répartition par fonction de l’utilisation de l’UC. Vous pouvez afficher les résultats de l’utilisation de l’UC quand l’exécution est suspendue, par exemple à un point d’arrêt.

Les instructions suivantes indiquent comment utiliser l’outil **Utilisation de l’UC** sans le débogueur, à l’aide du **Profileur de performances** de Visual Studio. Les exemples utilisent une build Release sur un ordinateur local. Les builds Release fournissent la meilleure vue des performances réelles de l’application. Pour analyser l’utilisation de l’UC avec des builds de débogage, consultez [Guide du débutant en profilage des performances](../profiling/beginners-guide-to-performance-profiling.md).

En règle générale, c’est l’ordinateur local qui réplique le mieux l’exécution des applications installées. Pour les applications Windows Phone, la collecte des données directement à partir de l’appareil fournit les données les plus précises. Pour collecter des données à partir d’un appareil distant, exécutez l’application directement sur l’appareil, et non par le biais d’une connexion Bureau à distance.

>[!NOTE]
>Windows 7 ou ultérieur est nécessaire pour utiliser le [Profileur de performances](../profiling/profiling-feature-tour.md).

##  <a name="collect-cpu-usage-data"></a>Collecter les données d'utilisation de l'UC

1. Dans le projet Visual Studio, affectez **Release** comme configuration de solution et sélectionnez **Ordinateur Local** comme cible de déploiement.

    ![Sélectionnez Release et Ordinateur Local](../profiling/media/cpuuse_selectreleaselocalmachine.png "Sélectionnez Release et Ordinateur Local")

1. Sélectionnez **Déboguer** > **Profileur de performances**.

1. Sous **Outils disponibles**, sélectionnez **Utilisation de l’UC**, puis **Démarrer**.

    ![Sélectionnez Utilisation de l’UC](../profiling/media/cpuuse_lib_choosecpuusage.png "Sélectionnez Utilisation de l’UC")

4. Une fois que l’application a démarré, la session de diagnostic commence et affiche les données d’utilisation de l’UC. Quand vous avez terminé la collecte des données, sélectionnez **Arrêter la collecte**.

   ![Arrêtez la collecte des données d’utilisation de l’UC](../profiling/media/cpu_use_wt_stopcollection.png "Arrêtez la collecte des données d’utilisation de l’UC")

   L'outil Utilisation de l'UC analyse les données et affiche le rapport.

   ![Rapport d’utilisation de l’UC](../profiling/media/cpu_use_wt_report.png "Rapport d’utilisation de l’UC")


## <a name="analyze-the-cpu-usage-report"></a>Analyser le rapport d'utilisation de l'UC

Le rapport de diagnostic est trié par **Total UC**, du plus élevé au plus bas. Changez l’ordre de tri ou la colonne de tri en sélectionnant les en-têtes de colonnes. Utiliser la liste déroulante **Filtre** pour sélectionner ou désélectionner des threads à afficher, et utilisez la zone **Rechercher** pour rechercher un nœud ou un thread spécifique.

###  <a name="BKMK_Call_tree_data_columns"></a> Colonnes de données d’utilisation de l’UC

|||
|-|-|
|**Total UC [unité, %]**|![% total, équation de données](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Millisecondes et pourcentage d’UC utilisés par les appels à la fonction, et fonctions appelées par la fonction, durant la plage de temps sélectionnée. Cette information est différente du graphe chronologique **Utilisation de l’UC**, qui compare l’activité totale de l’UC durant une plage de temps à la quantité totale d’UC disponible.|
|**Temps UC exclusif [unité, %]**|![% auto, équation](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Millisecondes et pourcentage d’UC utilisés par les appels à la fonction durant la plage de temps sélectionnée, à l’exclusion des fonctions appelées par la fonction.|
|**Module**|Nom du module contenant la fonction.

###  <a name="BKMK_The_CPU_Usage_call_tree"></a> Arborescence des appels d'utilisation du processeur

Pour afficher l’arborescence des appels, sélectionnez le nœud parent dans le rapport. La page **Utilisation de l’UC** s’ouvre sur la vue **Appelant/appelé**. Dans la liste déroulante **Affichage actuel**, sélectionnez **Arborescence des appels**.

####  <a name="BKMK_Call_tree_structure"></a> Structure de l’arborescence des appels

 ![Structure d’arborescence des appels](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "Structure d’arborescence des appels")

|||
|-|-|
|![Étape 1](../profiling/media/procguid_1.png "ProcGuid_1")|Le nœud de premier niveau des arborescences d’appels de l’outil Utilisation de l’UC est un pseudo-nœud.|
|![Étape 2](../profiling/media/procguid_2.png "ProcGuid_2")|Dans la plupart des applications, quand l’option **Afficher le code externe** est désactivée, le nœud de second niveau est un nœud **[Code externe]**. Le nœud contient le code système et framework qui démarre et arrête l’application, dessine l’interface utilisateur, contrôle la planification des threads et fournit d’autres services de bas niveau à l’application.|
|![Étape 3](../profiling/media/procguid_3.png "ProcGuid_3")|Les enfants du nœud de deuxième niveau sont les méthodes en code utilisateur et des routines asynchrones appelées ou créées par le code système et framework de deuxième niveau.|
|![Étape 4](../profiling/media/procguid_4.png "ProcGuid_4")|Les nœuds enfants d’une méthode ont des données seulement pour les appels de la méthode parente. Lorsque l'option **Afficher le Code externe** est désactivée, les méthodes d'application peuvent également contenir un nœud **[Code externe]** .|

####  <a name="BKMK_External_Code"></a> Code externe

 Les fonctions système et framework qui sont exécutées par votre code sont appelées *code externe*. Les fonctions de code externe démarrent et arrêtent l’application, dessinent l’interface utilisateur, contrôlent les threads et fournissent d’autres services de bas niveau à l’application. Dans la plupart des cas, vous ne serez pas intéressé par le code externe ; par conséquent, l’arborescence des appels de l’utilisation de l’UC regroupe les fonctions externes d’une méthode utilisateur en un seul nœud **[Code externe]** .

 Pour voir les chemins d’appel du code externe, sélectionnez **Afficher le code externe** dans la liste déroulante **Filtrer** de la page principale des rapports de diagnostic (volet droit), puis sélectionnez **Appliquer**. La vue **Arborescence des appels** de la page **Utilisation de l’UC** page étend alors les appels de code externe. (La liste déroulante **Filtrer** est disponible sur la page principale des diagnostics, et non sur les vues détaillées.)

 ![Afficher le code externe](../profiling/media/cpu_use_wt_filterview.png "Afficher le code externe")

 De nombreuses chaînes d’appels de code externe sont profondément imbriquées ; par conséquent, la largeur de la chaîne peut dépasser la largeur d’affichage de la colonne **Nom de la fonction**. Les noms des fonctions apparaissent alors comme **...**.

 ![Code externe imbriqué dans l’arborescence des appels](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "Code externe imbriqué dans l’arborescence des appels")

 Pour rechercher un nom de fonction, utilisez la zone de recherche. Placez le curseur sur la ligne sélectionnée ou utilisez la barre de défilement horizontale pour afficher les données.

 ![Rechercher du code externe imbriqué](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "Rechercher du code externe imbriqué")

###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Fonctions asynchrones de l'arborescence des appels de l'utilisation du processeur

 Quand le compilateur rencontre une méthode asynchrone, il crée une classe masquée pour contrôler l’exécution de la méthode. Conceptuellement, la classe est une machine à états. Elle a des fonctions générées par le compilateur qui appellent de façon asynchrone les méthodes d’origine ainsi que les rappels, le planificateur et les itérateurs nécessaires pour les exécuter. Quand une méthode parente appelle la méthode d’origine, le compilateur supprime la méthode du contexte d’exécution du parent et exécute les méthodes de la classe masquée dans le contexte du code système et framework qui contrôle l’exécution de l’application. Les méthodes asynchrones sont souvent, mais pas toujours, exécutées sur un ou plusieurs threads différents. Ce code est affiché dans l’arborescence des appels **Utilisation de l’UC** en tant qu’enfants du nœud **[Code externe]** situé immédiatement sous le nœud supérieur de l’arborescence.

Dans l’exemple suivant, les deux premiers nœuds sous **[Code externe]** sont les méthodes générées par le compilateur de la classe de la machine à états. Le troisième nœud est l’appel à la méthode d’origine.

![Nœud asynchrone](media/cpu_use_wt_getmaxnumberasync_selected.png "Nœud asynchrone")

Développez les méthodes générées pour voir ce qui se passe :

![Nœud asynchrone développé](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "Nœud asynchrone développé")

- `MainPage::GetMaxNumberAsyncButton_Click` gère simplement la liste des valeurs de la tâche, calcule le nombre maximal de résultats et affiche la sortie.

- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` affiche l'activité requise pour planifier et lancer les 48 tâches qui encapsulent l'appel à `GetNumberAsync`.

- `MainPage::<GetNumberAsync>b__b` affiche l’activité des tâches qui appellent `GetNumber`.
