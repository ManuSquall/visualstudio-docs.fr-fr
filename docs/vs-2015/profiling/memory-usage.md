---
title: Utilisation de la mémoire | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bbb58d6c-3362-4ca3-8e87-64b2d4415bf6
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0feabad8dfa3b086c9ed5a1a58e231719774f9cc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298356"
---
# <a name="memory-usage"></a>Utilisation de la mémoire
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Recherchez les fuites de mémoire et les utilisations inefficaces de la mémoire lors du débogage avec l'outil de diagnostic **Utilisation de la mémoire** intégré au débogueur. L’outil Utilisation de la mémoire vous permet de prendre un ou plusieurs *instantanés* du tas de mémoire managée et native. Vous pouvez collecter des instantanés d’applications .NET, natives ou en mode mixte (.NET et native).  
  
- Vous pouvez analyser un instantané pour comprendre l’impact relatif des types d’objets sur l’utilisation de la mémoire et pour rechercher le code dans votre application qui utilise la mémoire de manière inefficace.  
  
- Vous pouvez aussi comparer (diff) deux instantanés d’une application pour rechercher les sections de votre code qui provoquent une augmentation de l’utilisation de la mémoire au fil du temps.  
  
  L’illustration suivante montre la fenêtre **Outils de diagnostic** de Visual Studio 2015 Update 1 :  
  
  ![Outils&#45;Update 1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
  Bien que vous puissiez collecter des instantanés de la mémoire à tout moment dans l'outil **Utilisation de la mémoire**, vous pouvez utiliser le débogueur Visual Studio pour contrôler la façon dont votre application s'exécute lors de l'examen des problèmes de performances. La définition de points d’arrêt, l’exécution pas à pas, Interrompre tout et d’autres actions du débogueur peuvent vous aider à concentrer vos investigations en matière de performances sur les chemins du code qui sont les plus pertinents. Le fait d’effectuer ces actions pendant l’exécution de votre application peut éliminer le bruit du code qui ne vous intéresse pas et réduire considérablement la quantité de temps nécessaire pour diagnostiquer un problème.  
  
  Vous pouvez également utiliser l’outil Utilisation de la mémoire en dehors du débogueur. Consultez [Memory Usage without Debugging](https://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0).  
  
> [!NOTE]
> **Prise en charge des allocateurs personnalisés** Le profileur de mémoire native fonctionne en collectant des données d’événements [ETW](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) d’allocation émises pendant l’exécution.  Les allocateurs dans le CRT et le Kit de développement logiciel (SDK) Windows ont été annotés au niveau de la source afin que leurs données d’allocation puissent être capturées.  Si vous écrivez vos propres allocateurs, toutes les fonctions qui retournent un pointeur vers la mémoire du tas nouvellement allouée peuvent être décorées avec [__declspec](https://msdn.microsoft.com/library/832db681-e8e1-41ca-b78c-cd9d265cdb87)(allocator), comme illustré dans cet exemple pour myMalloc :  
>   
> `__declspec(allocator) void* myMalloc(size_t size)`  
  
## <a name="analyze-memory-use-with-the-debugger"></a>Analyser l’utilisation de la mémoire avec le débogueur  
  
> [!NOTE]
> Comme la collecte des données de la mémoire peut affecter les performances du débogage de vos applications natives ou en mode mixte, les instantanés de la mémoire sont désactivés par défaut. Pour activer les instantanés des applications natives ou en mode mixte, démarrez une session de débogage (touche de raccourci : **F5**). Quand la fenêtre **Outils de diagnostic** apparaît, choisissez l'onglet Utilisation de la mémoire, puis **Activer les instantanés**.  
>   
> ![Activer les instantanés](../profiling/media/dbgdiag-mem-mixedtoolbar-enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
>   
> Arrêtez (touche de raccourci : **Maj + F5**) et redémarrez le débogage.  
  
 Quand vous voulez capturer l'état de la mémoire, choisissez **Prendre un instantané** sur la barre d'outils de synthèse **Utilisation de la mémoire**.  
  
 ![Prendre un instantané](../profiling/media/dbgdiag-mem-mixedtoolbar-takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")  
  
> [!TIP]
> - Pour créer une ligne de base pour les comparaisons de mémoire, envisagez de prendre un instantané au démarrage de votre session de débogage.  
>   - Comme il peut être difficile de capturer le profil de mémoire d’une opération qui vous intéresse si votre application alloue et libère fréquemment de la mémoire, définissez des points d’arrêt au début et à la fin de l’opération ou bien exécutez pas à pas l’opération pour trouver le point exact où la mémoire a été modifiée.  
  
## <a name="viewing-memory-snapshot-details"></a>Affichage des détails d’un instantané de la mémoire  
 Les lignes de la table de résumé Utilisation de la mémoire répertorient les instantanés que vous avez pris pendant la session de débogage.  
  
 Les colonnes de la ligne varient selon le mode de débogage que vous choisissez dans les propriétés du projet : .NET, natif ou mixte (.NET et natif).  
  
- Les colonnes **Objets managés** et **Allocations natives** affichent le nombre d’objets dans la mémoire .NET et dans la mémoire native au moment où l’instantané a été pris.  
  
- Les colonnes **Taille du tas managé** et **Taille du tas natif** affichent le nombre d’octets dans les tas .NET et natif.  
  
- Quand vous avez pris plusieurs instantanés, les cellules du tableau récapitulatif contiennent la différence de valeur entre l’instantané d’une ligne et l’instantané précédent.  
  
   ![Cellule de table de résumé de la mémoire](../profiling/media/dbgdiag-mem-summarytablecell.png "DBGDIAG_MEM_SummaryTableCell")  
  
  **Pour afficher un rapport détaillé**  
  
- Pour afficher les détails de l’instantané sélectionné, choisissez le lien Actuel.  
  
- Pour afficher les détails de la différence entre l’instantané actuel et l’instantané précédent, cliquez sur le lien Modification.  
  
  Le rapport s’affiche dans une fenêtre distincte.  
  
## <a name="memory-usage-details-reports"></a>Rapports détaillés sur l’utilisation de la mémoire  
  
### <a name="managed-types-reports"></a>Rapports sur les types managés  
 Choisissez le lien Actuel d'une cellule **Objets managés** ou **Taille du tas managé** dans le tableau de résumé de l'utilisation de la mémoire.  
  
 ![Chemins d’accès du rapport &#45; de type managé du débogueur à la racine](../profiling/media/dbgdiag-mem-managedtypesreport-pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 Le volet du haut affiche le nombre et la taille des types de l'instantané, y compris la taille de tous les objets qui sont référencés par le type (**Taille inclusive**).  
  
 L’arborescence **Chemins d’accès à la racine** du volet du bas affiche les objets qui référencent le type sélectionné dans le volet du haut. Le Garbage Collector .NET Framework nettoie la mémoire pour un objet seulement quand le dernier type qui le référence a été publié.  
  
 L’arborescence **Types référencés** affiche les références qui sont détenues par le type sélectionné dans le volet du haut.  
  
 ![Vue rapport des types référencés managés](../profiling/media/dbgdiag-mem-managedtypesreport-referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 Pour afficher les instances d’un type sélectionné dans le volet supérieur, choisissez l’icône ![icône d’instance](../profiling/media/dbgdiag-mem-instanceicon.png "DBGDIAG_MEM_InstanceIcon") .  
  
 ![Vue instances](../profiling/media/dbgdiag-mem-managedtypesreport-instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 La vue **Instances** affiche les instances de l’objet sélectionné dans l’instantané dans le volet du haut. Les volets Chemins d’accès à la racine et Objets référencés affichent les objets qui référencent l’instance sélectionnée et les types référencés par l’instance sélectionnée. Quand le débogueur est arrêté du point où l’instantané a été pris, vous pouvez pointer sur la cellule Valeur pour afficher les valeurs de l’objet dans une info-bulle.  
  
### <a name="native-type-reports"></a>Rapports sur les types natifs  
 Cliquez sur le lien Actuel d'une cellule **Allocations native** ou **Taille du tas natif** dans la table de résumé de l'utilisation de la mémoire de la fenêtre **Outils de diagnostic**.  
  
 ![Affichage de type natif](../profiling/media/dbgdiag-mem-native-typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 L'**Affichage des types** affiche le nombre et la taille des types dans l'instantané.  
  
- Choisissez l’icône des instances (![l’icône d’instance dans la colonne type d’objet](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) d’un type sélectionné pour afficher des informations sur les objets du type sélectionné dans l’instantané.  
  
     La vue **Instances** affiche chaque instance du type sélectionné. La sélection d’une instance affiche la pile des appels qui a entraîné la création de l’instance dans le volet **Pile des appels d’allocation** .  
  
     ![Vue instances](../profiling/media/dbgdiag-mem-native-instances.png "DBGDIAG_MEM_Native_Instances")  
  
- Choisissez **Affichage des piles** dans la liste **Mode Affichage** pour afficher la pile des allocations pour le type sélectionné.  
  
     ![Affichage des piles](../profiling/media/dbgdiag-mem-native-stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>Rapports sur les modifications (Différences)  
  
- Cliquez sur le lien Modification dans une cellule de la table de résumé de l’onglet **Utilisation de la mémoire** dans la fenêtre **Outils de diagnostic** .  
  
   ![Choisir un rapport &#40;de&#41;modification Dif f](../profiling/media/dbgdiag-mem-choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
- Choisissez un instantané dans la liste **Comparer à** d’un rapport sur la mémoire managée ou native.  
  
   ![Choisissez un instantané dans la liste comparer à](../profiling/media/dbgdiag-mem-choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
  Le rapport des modifications ajoute des colonnes (marquées par la mention **(Diff)** ) au rapport de base, qui affichent la différence entre la valeur de l’instantané de base et celle de l’instantané comparé. Voici à quoi peut ressembler un rapport des différences de la vue des types natifs :  
  
  ![Types natifs diff natifs](../profiling/media/dbgdiag-mem-native-typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>Blogs et vidéos  
 [Diagnostic Tools debugger window in Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)  
  
 [Blog : Memory Usage Tool while debugging in Visual Studio 2015](https://devblogs.microsoft.com/devops/memory-usage-tool-while-debugging-in-visual-studio-2015/)  
  
 [Blog Visual C++ : Native Memory Diagnostics in VS2015 Preview](https://devblogs.microsoft.com/cppblog/native-memory-diagnostics-in-vs2015-preview/)  
  
 [Blog Visual C++ : Native Memory Diagnostic Tools for Visual Studio 2015 CTP](https://devblogs.microsoft.com/cppblog/native-memory-diagnostic-tools-for-visual-studio-14-ctp/)
