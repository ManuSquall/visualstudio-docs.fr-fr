---
title: Utilisation de la mémoire sans débogage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 24238fc0-40b8-4079-8579-698211db9a26
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64f739039d17af7fbee9718da93e8610e2619a85
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586949"
---
# <a name="memory-usage-without-debugging"></a>Utilisation de la mémoire sans débogage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser l’outil **Utilisation de la mémoire** sans débogage pour effectuer les opérations suivantes :  
  
- Surveiller l'utilisation de mémoire de vos applications directement dans Visual Studio quand vous développez un scénario.  
  
- Créer des instantanés détaillés de l’état de la mémoire de votre application.  
  
- Comparer des instantanés pour trouver la cause initiale des problèmes de mémoire.  
  
  Cette rubrique explique comment utiliser l’outil Utilisation de la mémoire pour analyser une application XAML universelle Windows. Si vous voulez analyser l’utilisation de la mémoire dans des applications universelles Windows qui utilisent JavaScript et HTML, consultez [Analyser l’utilisation de la mémoire (JavaScript)](https://msdn.microsoft.com/library/windows/apps/jj819176.aspx).  
  
## <a name="start-a-memory-usage-diagnostic-session"></a><a name="BKMK_Start_a_Memory_Usage_diagnostic_session"></a>Démarrer une session de diagnostic d’utilisation de la mémoire  
  
1. Ouvrez un projet Windows universel C# dans Visual Studio.  
  
2. Dans la barre de menus, choisissez **Déboguer/Profileur de performances...**  
  
3. Sélectionnez **Utilisation de la mémoire**, puis choisissez le bouton **Démarrer** situé en bas de la page.  
  
     ![Commencer une session de diagnostic de l'utilisation de la mémoire](../profiling/media/memuse-start-diagnosticssession.png "MEMUSE_Start_DiagnosticsSession")  
  
## <a name="monitor-memory-use"></a><a name="BKMK_Monitor_memory_use"></a>Surveiller l’utilisation de la mémoire  
 Même si vous pouvez utiliser l’outil **Utilisation de la mémoire** pour générer des rapports détaillés permettant d’identifier et de corriger des problèmes, il permet également d’étudier les effets en temps réel sur la mémoire d’un scénario que vous développez activement.  
  
 Quand vous démarrez une session de diagnostic, votre application démarre et la page **Outils de diagnostic** affiche un graphique chronologique de l’utilisation de la mémoire par votre application.  
  
 ![Page de vue d'ensemble de l'utilisation de la mémoire](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
 Le graphique chronologique montre les fluctuations de la mémoire de votre application pendant son exécution. Les pointes du graphique indiquent généralement que du code collecte ou crée des données, puis les supprime une fois le traitement terminé. Les pointes prononcées indiquent des zones que vous pourriez optimiser. Une hausse de la consommation de mémoire sans retour est plus préoccupante, car elle peut indiquer une utilisation inefficace de la mémoire ou une fuite de mémoire.  
  
### <a name="close-a-monitoring-session"></a><a name="BKMK_Close_a_monitoring_session"></a> Fermer une session de surveillance  
 ![Arrêter la collecte](../profiling/media/memuse-stopcollection.png "MEMUSE__StopCollection")  
  
 Pour arrêter une session de surveillance sans créer de rapport, fermez simplement la fenêtre de diagnostic. Pour générer un rapport quand vous avez créé des instantanés de la mémoire, choisissez **Arrêter**.  
  
## <a name="take-snapshots-of-the-memory-state-of-your-app"></a><a name="BKMK_Take_snapshots_to_analyze_the_memory_state_of_your_app"></a> Créer des instantanés de l’état de la mémoire de votre application  
 Si vous détectez un problème de mémoire que vous voulez examiner, vous pouvez prendre des instantanés pendant la session de diagnostic pour capturer des objets dans la mémoire à des moments précis. Dans la mesure où une application utilise un grand nombre de plusieurs types d'objets, il peut être utile de concentrer votre analyse sur un seul scénario. Il peut être également utile de disposer d'un instantané de référence de l'application avant qu'un problème de mémoire ne se produise, d'un autre instantané après la première occurrence du problème et d'un ou plusieurs instantanés supplémentaires si vous pouvez répéter le scénario.  
  
 Pour collecter des instantanés, démarrez une nouvelle session de diagnostic. Choisissez **Prendre un instantané** quand vous voulez capturer les données de mémoire. Pour générer un rapport, choisissez **Arrêter**.  
  
## <a name="memory-usage-overview-page"></a><a name="BKMK_Memory_Usage_overview_page"></a>Page vue d’ensemble de l’utilisation de la mémoire  
 Une fois que vous avez arrêté la collection des données, l’outil Utilisation de la mémoire arrête l’application et affiche le rapport de vue d’ensemble.  
  
 ![Page de vue d'ensemble de l'utilisation de la mémoire](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
### <a name="memory-usage-snapshot-views"></a><a name="BKMK_Memory_Usage_snapshot_views"></a> Vues d’instantanés d’utilisation de la mémoire  
 Vous utilisez les vues d'instantanés pour ouvrir des rapports détaillés dans de nouvelles fenêtres Visual Studio. Il existe deux types de vues d'instantanés :  
  
- Un [rapport détaillé d’instantané](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_details_reports) indique les types et les instances d’un seul instantané.  
  
- Un [rapport de comparaison d’instantanés](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_difference__diff__reports) compare les types et les instances de deux instantanés.  
  
  ![Liens de la vue Instantané](../profiling/media/memuse-snapshotview-numbered.png "MEMUSE__SnapshotView_Numbered")  
  
  Les éléments numérotés de l'image de la vue d'instantané sont des liens ouvrant les vues de rapport d'utilisation de la mémoire.  
  
|||  
|-|-|  
|![Étape 1](../profiling/media/procguid-1.png "ProcGuid_1")|Le texte du lien indique le nombre total d'octets dans la mémoire au moment où l'instantané a été pris.<br /><br /> Choisissez ce lien pour afficher un rapport détaillé de l'instantané, trié selon la taille totale des instances du type.|  
|![Étape 2](../profiling/media/procguid-2.png "ProcGuid_2")|Le texte du lien indique le nombre total d'objets dans la mémoire au moment où l'instantané a été pris.<br /><br /> Choisissez ce lien pour afficher un rapport détaillé de l'instantané, trié selon le nombre total d'instances des types.|  
|![Étape 3](../profiling/media/procguid-3.png "ProcGuid_3")|Le texte du lien indique la différence entre la taille totale des objets dans la mémoire au moment de l'instantané et la taille totale de l'instantané précédent.<br /><br /> Le texte du lien est un nombre positif quand la taille de la mémoire de cet instantané est supérieure à celle du précédent, et un nombre négatif quand la taille est inférieure. Le texte du lien **Planning de référence** indique que cet instantané est le premier de la session de diagnostic. **Aucune différence** indique que la différence est nulle.<br /><br /> Choisissez ce lien pour afficher un rapport différentiel des instantanés, trié selon la différence de taille totale des instances des types.|  
|![Étape 4](../profiling/media/procguid-4.png "ProcGuid_4")|Le texte du lien indique la différence entre le nombre total d'objets mémoire dans cet instantané et le nombre d'objets de l'instantané précédent.<br /><br /> Choisissez ce lien pour afficher un rapport différentiel des instantanés, trié selon le nombre total d'instances des types.|  
  
## <a name="snapshot-reports"></a><a name="BKMK_Snapshot_reports"></a> Rapports d’instantané  
 ![Rapport Instantané de l'utilisation de la mémoire](../profiling/media/memuse-snapshotreport-all.png "MEMUSE_SnapshotReport_All")  
  
### <a name="snapshot-report-trees"></a><a name="BKMK_Snapshot_report_trees"></a> Arborescences de rapport d’instantané  
  
#### <a name="managed-heap"></a><a name="BKMK_Managed_Heap"></a> Tas managé  
 Les arborescences de tas managé [Arborescence Tas managé (détails de l’instantané)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_details_) et [Arborescence Tas managé (comparaison d’instantanés)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_diff_) indiquent les types et instances présents dans le rapport. La sélection d’un type ou d’une instance affiche les arborescences **Chemins d’accès à la racine** et **Objets référencés** pour l’élément sélectionné.  
  
#### <a name="paths-to-root"></a><a name="BKMK_Paths_to_Root"></a>Chemins d’accès à la racine  
 L’[arborescence Chemins d’accès à la racine (détails de l’instantané)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_details_) et l’[arborescence Chemins d’accès à la racine (comparaison d’instantanés)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_diff_) affichent la chaîne d’objets qui font référence au type ou à l’instance. Le récupérateur de mémoire .NET Framework nettoie la mémoire d’un objet uniquement quand toutes les références à cet objet ont été libérées.  
  
#### <a name="referenced-objects"></a><a name="BKMK_Referenced_Objects"></a> Objets référencés  
 L’[arborescence Objets référencés (détails de l’instantané)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_details_) et l’[arborescence Objets référencés (comparaison d’instantanés)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_diff_) affichent les objets auxquels l’instance ou le type sélectionné fait référence.  
  
### <a name="object-type-and-instance-fields"></a><a name="BKMK_Object_Type_and_Instance_fields"></a> Champs Type d’objet et Instance  
 Quand une entrée **Type d’objet** comporte des entrées enfants, vous pouvez choisir l’icône fléchée pour les afficher. Si la couleur du texte **Type d’objet** est bleue, vous pouvez le choisir pour accéder à l’objet dans son fichier de code source. Le fichier source s'ouvre dans une fenêtre séparée.  
  
 Les noms d'instance sont des ID uniques générés par l'outil Utilisation de la mémoire.  
  
 Si vous notez un type difficilement identifiable ou si vous ne savez pas de quelle façon il est impliqué dans votre code, il s’agit probablement d’un objet du .NET Framework, du système d’exploitation ou du compilateur que l’outil Utilisation de la mémoire affiche, car il est impliqué dans les chaînes de propriétés de vos objets.  
  
### <a name="report-tree-filters"></a><a name="BKMK_Report_tree_filters_"></a> Filtres des arborescences de rapport  
 La plupart des applications contiennent un très grand nombre de types, dont une majorité n'est pas très utile au développeur d'application. L’outil **Utilisation de la mémoire** définit deux filtres permettant de masquer la plupart de ces types dans les arborescences **Tas managé** et **Chemins d’accès à la racine**. Vous pouvez également filtrer une arborescence par nom de type.  
  
 ![Options de tri et de filtre](../profiling/media/memuse-sortandfilter.png "MEMUSE_SortAndFilter")  
  
#### <a name="filter"></a><a name="BKMK_Filter"></a>Filtres  
 Entrez une chaîne dans la zone **Filtre** pour restreindre l’affichage des arborescences aux types qui contiennent le texte spécifié. Le filtre n'est pas sensible à la casse et reconnaît la chaîne spécifiée dans toutes les parties des noms de type.  
  
#### <a name="collapse-small-objects"></a><a name="BKMK_Collapse_Small_Objects"></a> Réduire les petits objets  
 Quand ce filtre est appliqué, les types dont la **Taille (octets)** est inférieure à 0,5 % de la taille totale de la mémoire de l’instantané sont masqués dans la liste **Tas managé**.  
  
#### <a name="just-my-code"></a><a name="BKMK_Just_My_Code"></a>Uniquement mon code  
 Le filtre **Uniquement mon code** masque la plupart des instances générées par du code externe. Les types externes sont détenus par le système d'exploitation ou les composants Framework. Ils peuvent aussi être générés par le compilateur.  
  
## <a name="snapshot-details-reports"></a><a name="BKMK_Snapshot_details_reports"></a> Rapports détaillés d’instantané  
 Vous utilisez un rapport détaillé d'instantané pour vous concentrer sur un seul instantané d'une session de diagnostic. Pour ouvrir un rapport détaillé, choisissez l'un des deux liens dans une vue d'instantané, comme indiqué dans l'image suivante. Les deux liens ouvrent le même rapport. La seule différence concerne l’ordre de tri de départ de l’arborescence **Tas managé** dans le rapport. Dans les deux cas, vous pouvez modifier l'ordre de tri après ouverture du rapport.  
  
 ![Liens vers le rapport d'instantané dans une vue Instantané](../profiling/media/memuse-snapshotview-snapshotdetailslinks.png "MEMUSE_SnapshotView_SnapshotDetailsLinks")  
  
- Le lien **Mo** trie le rapport en fonction de la colonne **Taille inclusive (octets)**.  
  
- Le lien **objets** trie le rapport en **calculant** la colonne nombre.  
  
### <a name="managed-heap-tree-snapshot-details"></a><a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> Arborescence Tas managé (détails de l’instantané)  
 L’arborescence **Tas managé** répertorie les types d’objets contenus dans la mémoire. Vous pouvez développer le nom d’un type pour afficher les dix instances du type les plus volumineuses, triées par taille. La sélection d’un type ou d’une instance affiche les arborescences **Chemins d’accès à la racine** et **Objets référencés** pour l’élément sélectionné.  
  
 ![Arborescence de tas managé](../profiling/media/memuse-snapshotdetails-managedheaptree.png "MEMUSE__SnapshotDetails_ManagedHeapTree")  
  
|||  
|-|-|  
|**Type d'objet**|Nom du type ou instance de l'objet.|  
|**Count**|Nombre d'instances d'objet du type. Le nombre est toujours égal à 1 pour une instance.|  
|**Taille (octets)**|Pour un type, taille de toutes les instances du type dans l'instantané de la mémoire, sans compter la taille des objets contenus dans les instances.<br /><br /> Pour une instance ou un type, taille de l'objet sans compter la taille des objets contenus dans l'instance. instances.|  
|**Taille inclusive (octets)**|Taille des instances du type ou taille d'une seule instance, y compris la taille des objets contenus.|  
  
### <a name="paths-to-root-tree-snapshot-details"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Arborescence Chemins d’accès à la racine (détails de l’instantané)  
 L’arborescence **Chemins d’accès à la racine** indique la chaîne d’objets faisant référence au type ou à l’instance. Le récupérateur de mémoire .NET Framework nettoie la mémoire d’un objet uniquement quand toutes les références à cet objet ont été libérées.  
  
 ![Arborescence Chemins d'accès à la racine pour les types](../profiling/media/memuse-snapshotdetails-type-pathstoroottree.png "MEMUSE_SnapshotDetails_Type_PathsToRootTree")  
  
 Quand vous affichez un type dans l’arborescence **Chemins d’accès à la racine**, le nombre d’objets des types qui comportent des références à ce type est affiché dans la colonne **Nombre de références**. La colonne n'apparaît pas quand vous analysez une instance.  
  
### <a name="referenced-objects-tree-snapshot-details"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Arborescence Objets référencés (détails de l’instantané)  
 L’arborescence **Objets référencés** indique les objets référencés par le type ou l’instance sélectionnés.  
  
 ![Arborescence des objets référencés pour les instances](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Type d’objet/Instance**|Nom du type ou instance de l'objet.|  
|**Taille (octets)**|Pour un type, taille de toutes les instances du type, sans compter la taille des objets contenus dans le type.<br /><br /> Pour une instance, taille de l'objet, sans compter la taille des objets contenus dans l'objet.|  
|**Taille inclusive (octets)**|Taille totale des instances du type ou taille de l'instance, y compris la taille des objets contenus.|  
  
## <a name="snapshot-difference-diff-reports"></a><a name="BKMK_Snapshot_difference__diff__reports"></a> Rapports différentiels d’instantanés  
 Un rapport différentiel d'instantanés indique les modifications entre un instantané principal et l'instantané qui a été pris immédiatement avant. Pour ouvrir un rapport différentiel, choisissez l'un des deux liens dans une vue d'instantané, comme indiqué dans l'image suivante. Les deux liens ouvrent le même rapport. La seule différence concerne l’ordre de tri de départ de l’arborescence **Tas managé** dans le rapport. Vous pouvez modifier l'ordre de tri après ouverture du rapport.  
  
 ![Liens vers le rapport de différences dans une vue Instantané](../profiling/media/memuse-snapshotview-snapshotdifflinks.png "MEMUSE_SnapshotView_SnapshotDiffLinks")  
  
- Le lien **Mo** trie le rapport en fonction de la colonne **Taille inclusive (octets)**.  
  
- Le lien **objets** trie le rapport en **calculant** la colonne nombre.  
  
### <a name="managed-heap-tree-snapshot-diff"></a><a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> Arborescence Tas managé (comparaison d’instantanés)  
 L’arborescence **Tas managé** répertorie les types d’objets contenus dans la mémoire. Vous pouvez développer le nom d’un type pour afficher les dix instances du type les plus volumineuses, triées par taille. La sélection d’un type ou d’une instance affiche les arborescences **Chemins d’accès à la racine** et **Objets référencés** pour l’élément sélectionné.  
  
 ![Arborescence Tas managé pour un type dans le rapport des différences](../profiling/media/memuse-snapshotdiff-type-heap.png "MEMUSE_SnapshotDiff_Type_Heap")  
  
 Notez que les colonnes **Nombre**, **Taille (octets)** et **Taille inclusive (octets)** ont été réduites dans l’image.  
  
|||  
|-|-|  
|**Type d'objet**|Nom du type ou instance de l'objet.|  
|**Count**|Nombre d'instances d'un type dans l'instantané principal. **Count** est toujours 1 pour une instance.|  
|**Différence de nombre**|Pour un type, différence du nombre d'instances du type entre l'instantané principal et l'instantané précédent. Le champ est vide pour une instance.|  
|**Taille (octets)**|Taille des objets dans l'instantané principal, sans compter la taille des objets contenus dans les objets. Pour un type, **Taille (octets)** et **Taille inclusive (octets)** sont les totaux des tailles des instances du type.|  
|**Diff. taille totale (octets)**|Pour un type, différence de taille totale des instances du type entre l'instantané principal et l'instantané précédent, sans compter la taille des objets contenus dans les instances. Le champ est vide pour une instance.|  
|**Taille inclusive (octets)**|Taille des objets dans l'instantané principal, y compris la taille des objets contenus dans les objets.|  
|**Diff. de taille inclusive (octets)**|Pour un type, différence de taille de toutes les instances du type entre l'instantané principal et l'instantané précédent, y compris la taille des objets contenus dans les objets. Le champ est vide pour une instance.|  
  
### <a name="paths-to-root-tree-snapshot-diff"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Arborescence Chemins d’accès à la racine (comparaison d’instantanés)  
 L’arborescence **Chemins d’accès à la racine** indique la chaîne d’objets faisant référence au type ou à l’instance. Le récupérateur de mémoire .NET Framework nettoie la mémoire d’un objet uniquement quand toutes les références à cet objet ont été libérées.  
  
 ![Arborescence Chemins d'accès à la racine pour les instances en mode d'affichage des différences](../profiling/media/memuse-snapshotdiff-pathstoroot-instance-all.png "MEMUSE_SnapshotDiff_PathsToRoot_Instance_All")  
  
### <a name="referenced-objects-tree-snapshot-diff"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Arborescence Objets référencés (comparaison d’instantanés)  
 L’arborescence **Objets référencés** indique les objets référencés par le type ou l’instance principaux.  
  
 ![Arborescence des objets référencés pour les instances](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Type d’objet/Instance**|Nom du type ou instance de l'objet.|  
|**Taille (octets)**|Pour une instance, taille de l'objet dans l'instantané principal, sans compter la taille des objets contenus dans l'instance.<br /><br /> Pour un type, taille totale des instances du type dans l'instantané principal, sans compter la taille des objets contenus dans l'instance.|  
|**Taille inclusive (octets)**|Taille des objets dans l'instantané principal, y compris la taille des objets contenus dans les objets.|  
  
## <a name="see-also"></a> Voir aussi  
 [Mémoire JavaScript](../profiling/javascript-memory.md)   
 [Analyser les performances de l’application](https://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)   
 [Exécuter les outils de diagnostic et de performances](https://msdn.microsoft.com/library/788279d8-f56b-40a0-9bef-facc3dfba471)   
 [Meilleures pratiques en matière de performances pour les applications du Windows Store en C++, C# et Visual Basic](https://msdn.microsoft.com/library/windows/apps/hh750313.aspx)   
 [Diagnostic des problèmes de mémoire avec le nouvel outil Utilisation de la mémoire de Visual Studio](https://devblogs.microsoft.com/devops/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio/)
