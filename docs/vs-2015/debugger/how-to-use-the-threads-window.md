---
title: 'Comment : utiliser la fenêtre threads | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da41524fcb231ea399dbbd2a2904afd935e5c4f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824254"
---
# <a name="how-to-use-the-threads-window"></a>Comment : utiliser la fenêtre Threads
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans la fenêtre **Threads** , vous pouvez examiner et utiliser des threads dans l’application que vous déboguez.  
  
 La fenêtre **Threads** contient une table dans laquelle chaque ligne représente un thread dans votre application. Par défaut, ce tableau répertorie tous les threads de votre application, mais vous pouvez filtrer la liste de façon à afficher uniquement les threads qui vous intéressent. Chaque colonne contient un type d'informations différent. Vous pouvez également masquer certaines colonnes. Si vous affichez toutes les colonnes, les informations suivantes s'affichent, de gauche à droite :  
  
- La colonne d'indicateur, où vous pouvez marquer un thread auquel vous souhaitez apporter une attention spéciale. Pour plus d’informations sur la façon de marquer un thread, consultez [Comment : baliser et supprimer les indicateurs de threads](../debugger/how-to-flag-and-unflag-threads.md).  
  
- La colonne de thread active, où une flèche jaune indique un thread actif. Un contour de flèche indique le thread où l'exécution s'est arrêtée dans le débogueur.  
  
- La colonne **ID** , qui contient le numéro d’identification pour chaque thread.  
  
- La colonne **ID managé** , qui contient les numéros d’identification managés pour les threads managés.  
  
- La colonne **Category** , qui classe les threads comme des threads d’interface utilisateur, des gestionnaires d’appel de procédure distante ou des threads de travail. Une catégorie spéciale identifie le thread principal de l'application.  
  
- La colonne **Name** , qui identifie chaque thread par son nom, s’il en a un, ou comme \<No Name> .  
  
- La colonne **emplacement** , qui indique où le thread est en cours d’exécution. Vous pouvez développer cet emplacement de façon à afficher l’ensemble de la pile des appels du thread.  
  
- La colonne **priorité** , qui contient la priorité ou la priorité que le système a affecté à chaque thread.  
  
- La colonne **affinity mask** , qui est une colonne avancée généralement masquée. Cette colonne indique le masque d'affinité de processeur pour chaque thread. Dans un système multiprocesseurs, le masque d'affinité détermine les processeurs sur lesquels un thread peut s'exécuter.  
  
- La colonne **compteur suspendu** , qui contient le compteur suspendu. Ce compteur détermine si un thread peut s'exécuter. Pour obtenir une explication sur le compteur suspendu, consultez « Gel et libération des threads » plus loin dans cette rubrique.  
  
- La colonne **nom du processus** , qui contient le processus auquel appartient chaque thread. Cette colonne peut être utile lorsque vous déboguez plusieurs processus, mais elle est généralement masquée.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Pour afficher la fenêtre Threads en mode arrêt ou en mode exécution  
  
- Dans le menu **Déboguer** , pointez sur **fenêtres**, puis cliquez sur **Threads**.  
  
### <a name="to-display-or-hide-a-column"></a>Pour afficher ou masquer une colonne  
  
- Dans la barre d’outils en haut de la fenêtre **Threads** , cliquez sur **colonnes**, puis activez ou désactivez le nom de la colonne que vous souhaitez afficher ou masquer.  
  
### <a name="to-switch-the-active-thread"></a>Pour basculer le thread actif  
  
- Effectuez l'une des étapes suivantes :  
  
  - Double-cliquez sur un thread.  

  - Cliquez avec le bouton droit sur un thread, puis cliquez sur **basculer vers le thread**.  

    La flèche jaune s'affiche en regard du nouveau thread actif. Un contour gris de flèche identifie le thread où l'exécution s'est arrêtée dans le débogueur.  
  
## <a name="grouping-and-sorting-threads"></a>Regroupement et tri de threads  
 Lorsque vous regroupez des threads, un titre s'affiche dans le tableau pour chaque groupe. Ce titre contient une description du groupe, telle que « Thread de travail » ou « Threads sans indicateur », ainsi qu'un contrôle d'arborescence. Les threads membres de chaque groupe apparaissent sous le titre approprié. Si vous souhaitez masquer les threads membres d’un groupe, vous pouvez utiliser le contrôle d’arborescence pour réduire ce groupe.  
  
 Étant donné que le regroupement est prioritaire sur le tri, vous pouvez grouper des threads par catégorie, par exemple, puis les trier par ID dans chaque catégorie.  
  
#### <a name="to-sort-threads"></a>Pour trier des threads  
  
1. Dans la barre d’outils en haut de la fenêtre **Threads** , cliquez sur le bouton en haut de toute colonne.  
  
     Les threads sont alors triés en fonction des valeurs de la colonne choisie.  
  
2. Si vous souhaitez inverser l'ordre de tri, cliquez de nouveau sur le bouton.  
  
     Les threads qui figuraient au début de la liste s'affichent maintenant à la fin.  
  
#### <a name="to-group-threads"></a>Pour regrouper des threads  
  
- Dans la barre d’outils de la fenêtre **Threads** , cliquez sur la liste **regrouper par** , puis cliquez sur les critères par lesquels vous souhaitez regrouper les threads.  
  
#### <a name="to-sort-threads-within-groups"></a>Pour trier des threads au sein de groupes  
  
1. Dans la barre d’outils en haut de la fenêtre **Threads** , cliquez sur la liste **regrouper par** , puis cliquez sur les critères par lesquels vous souhaitez regrouper les threads.  
  
2. Dans la fenêtre **Threads** , cliquez sur le bouton situé en haut de toute colonne.  
  
     Les threads sont alors triés en fonction des valeurs de la colonne choisie.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Pour développer ou réduire tous les groupes  
  
- Dans la barre d’outils en haut de la fenêtre **Threads** , cliquez sur **développer les groupes** ou **réduire les groupes**.  
  
## <a name="searching-for-specific-threads"></a>Recherche de threads spécifiques  
 Dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], vous pouvez rechercher des threads qui correspondent à une chaîne spécifiée. Lorsque vous recherchez des threads dans la fenêtre **Threads** , la fenêtre affiche tous les threads qui correspondent à la chaîne recherchée dans n’importe quelle colonne. Ces informations incluent l’emplacement du thread qui apparaît en haut de la pile des appels dans la colonne **emplacement** . Par défaut, cependant, la recherche ne porte pas sur l'ensemble de la pile des appels.  
  
#### <a name="to-search-for-specific-threads"></a>Pour rechercher des threads spécifiques  
  
- Dans la barre d’outils en haut de la fenêtre **Threads**, accédez à la zone **Rechercher** et effectuez l’une des opérations suivantes :  
  
  - Tapez une chaîne recherchée et appuyez sur ENTRÉE.  

    \- ou -  

  - Cliquez sur la liste déroulante en regard de la zone de **recherche** et sélectionnez une chaîne de recherche à partir d’une recherche précédente.  
  
- (Facultatif) Pour inclure l’ensemble de la pile des appels dans la recherche, sélectionnez **Rechercher la pile des appels**.  
  
## <a name="freezing-and-thawing-threads"></a>Gel et libération des threads  
 Lorsque vous gelez un thread, le système ne démarre pas son exécution même si les ressources sont disponibles.  
  
 En code natif, vous pouvez interrompre ou reprendre des threads en appelant les fonctions Windows `SuspendThread` et `ResumeThread` ou les fonctions MFC [CWinThread :: SuspendThread](https://msdn.microsoft.com/library/57189c7e-fd71-42e5-bc4b-3de7cd373d28) et [CWinThread :: ResumeThread](https://msdn.microsoft.com/library/d6f97a2f-5c9f-4ee1-b978-d74938784db5). Si vous appelez `SuspendThread` ou `ResumeThread` , vous modifiez le *compteur suspendu*, qui s’affiche dans la fenêtre **Threads** . Toutefois, si vous gelez ou libérez un thread natif, vous ne changez pas le compteur suspendu. En code natif, un thread ne peut pas s'exécuter sauf s'il est libéré et que son compteur suspendu est égal à zéro.  
  
 En code managé, le gel ou la libération d'un thread modifie le compteur suspendu. En code managé, un thread gelé possède un compteur suspendu de 1. En code natif, un thread gelé possède un compteur suspendu de 0, à moins qu'il ait été interrompu par un appel `SuspendThread`.  
  
> [!NOTE]
> Lors du débogage d'un appel entre code natif et code managé, le code managé s'exécute dans le même thread physique que le code natif qui l'a appelé. Si vous suspendez ou figez le thread natif, le code managé sera également figé.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Pour geler ou libérer l'exécution d'un thread  
  
- Dans la barre d’outils en haut de la fenêtre **Threads** , cliquez sur **figer les threads** ou **libérer les threads**.  
  
     Cette action affecte uniquement les threads sélectionnés dans la fenêtre **Threads**.  
  
## <a name="displaying-flagged-threads"></a>Affichage des threads avec indicateur  
 Vous pouvez signaler un thread auquel vous souhaitez accorder une attention particulière en le marquant avec une icône dans la fenêtre **Threads**. Pour plus d’informations, consultez [Comment : baliser et supprimer les indicateurs de threads](../debugger/how-to-flag-and-unflag-threads.md). Dans la fenêtre Threads, vous pouvez choisir d'afficher tous les threads ou uniquement les threads avec indicateur.  
  
#### <a name="to-display-only-flagged-threads"></a>Pour afficher seulement les threads avec indicateur  
  
- Choisissez le bouton indicateur dans l’angle supérieur gauche de la fenêtre **Threads** .  
  
## <a name="displaying-thread-call-stacks-and-switching-between-frames"></a>Affichage des piles d'appel de thread et commutation entre les frames  
 Dans un programme multithread, chaque thread possède sa propre pile d'appel. La fenêtre **Threads** permet d’afficher facilement ces piles.  
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>Pour afficher la pile d'appel d'un thread  
  
- Dans la colonne **emplacement** , cliquez sur le triangle inversé en regard de l’emplacement du thread.  
  
     L'emplacement se développe pour indiquer la pile des appels du thread.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Pour afficher ou réduire les piles d‘appels de tous les threads  
  
- Dans la barre d’outils en haut de la fenêtre **Threads** , cliquez sur **développer les piles d’appels** ou réduire les piles d' **appels**.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer des applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procédure pas à pas : débogage d’une application multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md)
