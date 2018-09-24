---
title: Afficher les Threads dans le débogueur | Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b464213f6443ecbdf07c225fc3698697e91b5c11
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673244"
---
# <a name="view-threads-in-the-debugger-in-visual-studio-using-the-threads-window"></a>Afficher les Threads dans le débogueur dans Visual Studio à l’aide de la fenêtre Threads
Dans le **Threads** fenêtre, vous pouvez examiner et utiliser les threads de l’application que vous déboguez. Pour obtenir des instructions sur la façon d’utiliser le **Threads** fenêtre, consultez [procédure pas à pas : déboguer à l’aide de la fenêtre Threads](../debugger/how-to-use-the-threads-window.md).
  
 Le **Threads** fenêtre contient un tableau où chaque ligne représente un thread dans votre application. Par défaut, ce tableau répertorie tous les threads de votre application, mais vous pouvez filtrer la liste de façon à afficher uniquement les threads qui vous intéressent. Chaque colonne contient un type d'informations différent. Vous pouvez également masquer certaines colonnes. Si vous affichez toutes les colonnes, les informations suivantes s'affichent, de gauche à droite :  
  
-   La colonne d'indicateur, où vous pouvez marquer un thread auquel vous souhaitez apporter une attention spéciale. Pour plus d’informations sur la façon de signaler un thread, consultez [Comment : indicateur et les Threads sans indicateur](../debugger/how-to-flag-and-unflag-threads.md).  
  
-   Colonne de thread active, dans lequel une flèche jaune indique que le thread actuel (un contour de flèche indique le contexte actuel du débogueur pour un thread non actuel).
  
-   Le **ID** colonne qui contient le numéro d’identification pour chaque thread.  
  
-   Le **ID managé** colonne qui contient les numéros d’identification managés des threads managés.  
  
-   Le **catégorie** colonne, qui classe les threads en tant que threads d’interface utilisateur, gestionnaires d’appel de procédure distante ou threads de travail. Une catégorie spéciale identifie le thread principal de l'application.  
  
-   Le **nom** colonne qui identifie chaque thread par son nom, le cas échéant, ou en tant que \<sans nom >.  
  
-   Le **emplacement** colonne, qui indique où le thread est en cours d’exécution. Vous pouvez développer cet emplacement de façon à afficher l’ensemble de la pile des appels du thread.  
  
-   Le **priorité** colonne qui contient la priorité ou précédence que le système a assignée à chaque thread.  
  
-   Le **masque d’affinité** colonne, qui est une colonne avancée (généralement masquée). Cette colonne indique le masque d'affinité de processeur pour chaque thread. Dans un système multiprocesseurs, le masque d'affinité détermine les processeurs sur lesquels un thread peut s'exécuter.  
  
-   Le **compteur suspendu** (généralement masquée), de la colonne qui contient le compteur suspendu et est généralement masquée. Ce compteur détermine si un thread peut s'exécuter. Pour obtenir une explication sur le compteur suspendu, consultez « Gel et libération des threads » plus loin dans cette rubrique.  
  
-   Le **nom de processus** (généralement masquée), de la colonne qui contient le processus auquel chaque thread appartient. Cette colonne peut être utile lorsque vous déboguez plusieurs processus.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Pour afficher la fenêtre Threads en mode arrêt ou en mode exécution  
  
-   Pendant le débogage, sélectionnez le **déboguer** menu, pointez sur **Windows**, puis cliquez sur **Threads**.  
  
### <a name="to-display-or-hide-a-column"></a>Pour afficher ou masquer une colonne  
  
-   Dans la barre d’outils en haut de la **Threads** fenêtre, cliquez sur **colonnes**, puis activez ou désactivez le nom de la colonne que vous souhaitez afficher ou masquer.    

## <a name="display-flagged-threads"></a>Afficher les Threads avec indicateur  
 Vous pouvez signaler un thread auquel vous souhaitez accorder une attention particulière en le marquant avec une icône dans le **Threads** fenêtre. Pour plus d’informations, consultez [Comment : indicateur et les Threads sans indicateur](../debugger/how-to-flag-and-unflag-threads.md). Dans le **Threads** fenêtre que vous pouvez choisir d’afficher tous les threads ou uniquement les threads avec indicateur.  
  
#### <a name="to-display-only-flagged-threads"></a>Pour afficher seulement les threads avec indicateur  
  
-   Choisissez le **afficher les Threads avec indicateur uniquement** bouton en haut de la **Threads** fenêtre. (Si elle est grisée, vous devez signaler tout d’abord des certains threads.) 

## <a name="freeze-and-thaw-threads"></a>Figer et libérer les Threads  
 Lorsque vous gelez un thread, le système ne démarre pas son exécution même si les ressources sont disponibles.  
  
 En code natif, vous pouvez suspendre ou reprendre des threads en appelant les fonctions Windows `SuspendThread` et `ResumeThread` ou les fonctions MFC [CWinThread::SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) et [CWinThread::ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). Si vous appelez `SuspendThread` ou `ResumeThread`, vous modifiez le *compteur suspendu*, qui s’affiche dans le **Threads** fenêtre. Toutefois, si vous gelez ou libérez un thread natif, vous ne changez pas le compteur suspendu. En code natif, un thread ne peut pas s'exécuter sauf s'il est libéré et que son compteur suspendu est égal à zéro.  
  
 En code managé, le gel ou la libération d'un thread modifie le compteur suspendu. En code managé, un thread gelé possède un compteur suspendu de 1. En code natif, un thread gelé possède un compteur suspendu de 0, à moins qu'il ait été interrompu par un appel `SuspendThread`.  
  
> [!NOTE]
>  Lors du débogage d'un appel entre code natif et code managé, le code managé s'exécute dans le même thread physique que le code natif qui l'a appelé. Si vous suspendez ou figez le thread natif, le code managé sera également figé.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Pour geler ou libérer l'exécution d'un thread  
  
-   Dans la barre d’outils en haut de la **Threads** fenêtre, cliquez sur **figer les Threads** ou **libérer les Threads**.  
  
     Cette action affecte uniquement les threads qui sont sélectionnés dans le **Threads** fenêtre. 

### <a name="switch-to-another-thread"></a>Basculer vers un autre thread 

Une flèche jaune indique le thread actuel (et l’emplacement du pointeur d’exécution). Une flèche verte avec extrémité recourbée indique un thread non actuel possède le contexte du débogueur actuel.

#### <a name="to-switch-to-another-thread"></a>Pour basculer vers un autre thread  
  
-   Effectuez l'une des étapes suivantes :  
  
    -   Double-cliquez sur un thread.  
  
    -   Cliquez sur un thread et sur **basculer vers Thread**.

## <a name="group-and-sort-threads"></a>Groupe et les Threads de tri  
 Lorsque vous regroupez des threads, un titre s'affiche dans le tableau pour chaque groupe. Ce titre contient une description du groupe, telle que « Thread de travail » ou « Threads sans indicateur », ainsi qu'un contrôle d'arborescence. Les threads membres de chaque groupe apparaissent sous le titre approprié. Si vous souhaitez masquer les threads membres d'un groupe, vous pouvez utiliser le contrôle d'arborescence pour réduire ce groupe.  
  
 Étant donné que le regroupement est prioritaire sur le tri, vous pouvez grouper des threads par catégorie, par exemple, puis les trier par ID dans chaque catégorie.  
  
#### <a name="to-sort-threads"></a>Pour trier des threads  
  
1.  Dans la barre d’outils en haut de la **Threads** fenêtre, cliquez sur le bouton en haut de n’importe quelle colonne.  
  
     Les threads sont alors triés en fonction des valeurs de la colonne choisie.  
  
2.  Si vous souhaitez inverser l'ordre de tri, cliquez de nouveau sur le bouton.  
  
     Les threads qui figuraient au début de la liste s'affichent maintenant à la fin.  
  
#### <a name="to-group-threads"></a>Pour regrouper des threads  
  
-   Dans le **Threads** barre d’outils de la fenêtre, cliquez sur le **Group by** liste, puis cliquez sur les critères que vous souhaitez le regroupement des threads.  
  
#### <a name="to-sort-threads-within-groups"></a>Pour trier des threads au sein de groupes  
  
1.  Dans la barre d’outils en haut de la **Threads** fenêtre, cliquez sur le **Group by** liste, puis cliquez sur les critères que vous souhaitez le regroupement des threads.  
  
2.  Dans le **Threads** fenêtre, cliquez sur le bouton en haut de n’importe quelle colonne.  
  
     Les threads sont alors triés en fonction des valeurs de la colonne choisie.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Pour développer ou réduire tous les groupes  
  
-   Dans la barre d’outils en haut de la **Threads** fenêtre, cliquez sur **développer les groupes** ou **réduire les groupes**.  
  
## <a name="search-for-specific-threads"></a>Rechercher des Threads spécifiques  
 Dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], vous pouvez rechercher des threads qui correspondent à une chaîne spécifiée. Lorsque vous recherchez des threads dans le **Threads** , la fenêtre affiche tous les threads qui correspondent à la chaîne de recherche dans n’importe quelle colonne. Que les informations incluent l’emplacement de thread qui s’affiche en haut de la pile des appels dans le **emplacement** colonne. Par défaut, toutefois, la pile des appels ne porte pas.  
  
#### <a name="to-search-for-specific-threads"></a>Pour rechercher des threads spécifiques  
  
-   Dans la barre d’outils en haut de la **Threads** fenêtre, accédez à la **recherche** boîte et soit :  
  
    -   Tapez une chaîne recherchée et appuyez sur ENTRÉE.  
  
         \- ou -  
  
    -   Cliquez sur la liste déroulante en regard du **recherche** zone, puis sélectionnez une chaîne de recherche à partir d’une recherche précédente.  
  
-   (Facultatif) Pour inclure la pile des appels complète dans votre recherche, sélectionnez **rechercher la pile des appels**.   
  
## <a name="display-thread-call-stacks-and-switching-between-frames"></a>Afficher les piles d’appels de Thread et commutation entre les Frames  
Dans un programme multithread, chaque thread possède sa propre pile d'appel. Le **Threads** fenêtre fournit un moyen pratique d’afficher ces piles.

> [!TIP]
> Pour obtenir une représentation visuelle de la pile des appels pour chaque thread, utilisez la [piles parallèles](../debugger/get-started-debugging-multithreaded-apps.md) fenêtre.
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>Pour afficher la pile d'appel d'un thread  
  
-   Dans le **emplacement** colonne, cliquez sur le triangle inversé en regard de l’emplacement de thread.  
  
     L’emplacement se développe pour indiquer la pile des appels du thread.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Pour afficher ou réduire les piles d‘appels de tous les threads  
  
-   Dans la barre d’outils en haut de la **Threads** fenêtre, cliquez sur **développer la pile des appels** ou **réduire la pile des appels**.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer les Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Commencer à déboguer une application multithread](../debugger/get-started-debugging-multithreaded-apps.md)