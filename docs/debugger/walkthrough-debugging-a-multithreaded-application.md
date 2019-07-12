---
title: Afficher les threads dans le débogueur | Microsoft Docs
ms.date: 10/29/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f65bd7a904f30f132f654b6dd718532d9d0e66e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821587"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window-c-visual-basic-c"></a>Afficher les threads dans le débogueur Visual Studio à l’aide de la fenêtre Threads (C#, Visual Basic, C++)
Dans le **Threads** fenêtre, vous pouvez examiner et utiliser les threads de l’application que vous déboguez. Pour obtenir des instructions sur la façon d’utiliser le **Threads** fenêtre, consultez [procédure pas à pas : Déboguer à l’aide de la fenêtre Threads](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>Utiliser la fenêtre Threads
 Le **Threads** fenêtre contient un tableau où chaque ligne décrit un thread distinct dans votre application. Par défaut, ce tableau répertorie tous les threads de votre application, mais vous pouvez filtrer la liste de façon à afficher uniquement les threads qui vous intéressent. Chaque colonne décrit un type différent d’informations. Vous pouvez également masquer certaines colonnes. Si vous affichez toutes les colonnes, les colonnes suivantes s’affichent, de gauche à droite :

- **Indicateur**: Dans cet article sans étiquette, vous pouvez marquer un thread auquel vous souhaitez une attention particulière. Pour plus d’informations sur la façon de signaler un thread, consultez [Comment : Et supprimer les indicateurs threads](../debugger/how-to-flag-and-unflag-threads.md).

- **Thread actuel**: Dans cet article sans étiquette, une flèche jaune indique que le thread actuel. Un contour de flèche indique le contexte actuel du débogueur pour un thread non actuel.

- **ID** : Affiche le numéro d’identification pour chaque thread.

- **ID géré**: Affiche les numéros d’identification managés des threads managés.

- **Catégorie**: Affiche la catégorie de threads comme threads d’interface utilisateur, gestionnaires d’appel de procédure distante ou threads de travail. Une catégorie spéciale identifie le thread principal de l'application.

- **Nom** : Identifie chaque thread par son nom, le cas échéant, ou en tant que \<sans nom >.

- **Emplacement** : Indique où le thread est en cours d’exécution. Vous pouvez développer cet emplacement de façon à afficher l’ensemble de la pile des appels du thread.

- **Priorité**: Une colonne avancée (masquée par défaut) affiche la priorité ou précédence que le système a assignée à chaque thread.

- **Masque d’affinité**: Une colonne avancée (masquée par défaut), qui affiche le masque d’affinité de processeur pour chaque thread. Dans un système multiprocesseurs, le masque d'affinité détermine les processeurs sur lesquels un thread peut s'exécuter.

- **Compteur suspendu**: Une colonne avancée (masquée par défaut) affiche le compteur suspendu. Ce compteur détermine si un thread peut s'exécuter. Pour plus d’informations sur les calculs suspendus, consultez [figer et libérer les threads](#freeze-and-thaw-threads).

- **Nom du processus**: Une colonne avancée (masquée par défaut) affiche le processus auquel chaque thread appartient. Les données de cette colonne peuvent être utiles lorsque vous déboguez plusieurs processus.

- **ID de processus**: Une colonne avancée (masquée par défaut) qui affiche l’ID de processus auquel chaque thread appartient.

- **Qualificateur de transport**: Une colonne avancée (masquée par défaut) qui identifie de façon unique identifie l’ordinateur auquel le débogueur est connecté.

### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Pour afficher la fenêtre Threads en mode arrêt ou en mode exécution

- Lorsque Visual Studio est en mode débogage, sélectionnez le **déboguer** menu, pointez sur **Windows**, puis sélectionnez **Threads**.

### <a name="to-display-or-hide-a-column"></a>Pour afficher ou masquer une colonne

- Dans la barre d’outils en haut de la **Threads** fenêtre, sélectionnez **colonnes**. Ensuite, activez ou désactivez le nom de la colonne que vous souhaitez afficher ou masquer.

## <a name="display-flagged-threads"></a>Afficher les threads avec indicateur
 Vous pouvez signaler un thread auquel vous souhaitez accorder une attention particulière en le marquant avec une icône dans la fenêtre **Threads**. Pour plus d'informations, voir [Procédure : ajouter et supprimer les indicateurs des threads](../debugger/how-to-flag-and-unflag-threads.md). Dans la fenêtre **Threads**, vous pouvez choisir d’afficher tous les threads ou uniquement les threads avec indicateur.

### <a name="to-display-only-flagged-threads"></a>Pour afficher seulement les threads avec indicateur

- Choisissez **afficher les Threads avec indicateur uniquement** dans la barre d’outils en haut de la **Threads** fenêtre. (Si elle est grisée, vous devez signaler tout d’abord des certains threads.)

## <a name="freeze-and-thaw-threads"></a>Figer et libérer les threads
 Lorsque vous gelez un thread, le système ne démarre pas l’exécution du thread même si les ressources sont disponibles.

 En code natif, vous pouvez suspendre ou reprendre des threads en appelant les fonctions Windows `SuspendThread` et `ResumeThread`. Ou, appelez les fonctions MFC [CWinThread::SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) et [CWinThread::ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). Si vous appelez `SuspendThread` ou `ResumeThread`, le *compteur suspendu* indiqué dans le **Threads** fenêtre sera modifiée. Le compteur suspendu ne change pas si vous gelez ou libérez un thread natif. Impossible d’exécuter un thread en code natif, sauf si elle est libéré et possède un compteur suspendu de zéro.

 Dans le code managé, le compteur suspendu change lorsque vous gelez ou libérez un thread. Si vous gelez un thread dans du code managé, son compteur suspendu est 1. Lorsque vous gelez un thread en code natif, son compteur suspendu est 0, sauf si vous avez utilisé le `SuspendThread` appeler.

> [!NOTE]
> Lors du débogage d'un appel entre code natif et code managé, le code managé s'exécute dans le même thread physique que le code natif qui l'a appelé. Si vous suspendez ou figez le thread natif, le code managé sera également figé.

### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Pour geler ou libérer l'exécution d'un thread

- Dans la barre d’outils en haut de la **Threads** fenêtre, sélectionnez **figer les Threads** ou **libérer les Threads**.

     Cette action affecte uniquement les threads sélectionnés dans la fenêtre **Threads**.

### <a name="switch-to-another-thread"></a>Basculer vers un autre thread

Une flèche jaune indique le thread actuel (et l’emplacement du pointeur d’exécution). Une flèche verte avec extrémité recourbée indique un thread non actuel possède le contexte du débogueur actuel.

#### <a name="to-switch-to-another-thread"></a>Pour basculer vers un autre thread

- Suivre une des étapes suivantes :

  - Double-cliquez sur un thread.

  - Cliquez sur un thread et sélectionnez **commutateur à Thread**.

## <a name="group-and-sort-threads"></a>Regrouper et trier des threads
 Lorsque vous regroupez des threads, un titre s'affiche dans le tableau pour chaque groupe. Ce titre contient une description du groupe, telle que **Thread de travail** ou **Threads sans indicateur**, ainsi qu’un contrôle d’arborescence. Les threads membres de chaque groupe apparaissent sous le titre approprié. Si vous souhaitez masquer les threads membres d’un groupe, utilisez le contrôle d’arborescence pour réduire ce groupe.

 Étant donné que le regroupement est prioritaire sur le tri, vous pouvez grouper des threads par catégorie, par exemple, puis les trier par ID dans chaque catégorie.

### <a name="to-sort-threads"></a>Pour trier des threads

1. Dans la barre d’outils en haut de la **Threads** fenêtre, sélectionnez le bouton en haut de n’importe quelle colonne.

     Les threads sont alors triés en fonction des valeurs de la colonne choisie.

2. Si vous souhaitez inverser l’ordre de tri, sélectionnez à nouveau le même bouton.

     Les threads qui figuraient au début de la liste s'affichent maintenant à la fin.

### <a name="to-group-threads"></a>Pour regrouper des threads

- Dans le **Threads** barre d’outils, sélectionnez le **Group by** liste, puis sélectionnez les critères que vous souhaitez le regroupement des threads.

### <a name="to-sort-threads-within-groups"></a>Pour trier des threads au sein de groupes

1. Dans la barre d’outils en haut de la **Threads** fenêtre, sélectionnez le **Group by** liste, puis sélectionnez les critères que vous souhaitez le regroupement des threads.

2. Dans le **Threads** fenêtre, sélectionnez le bouton en haut de n’importe quelle colonne.

     Les threads sont alors triés en fonction des valeurs de la colonne choisie.

### <a name="to-expand-or-collapse-all-groups"></a>Pour développer ou réduire tous les groupes

- Dans la barre d’outils en haut de la **Threads** fenêtre, sélectionnez **développez groupes** ou **réduire les groupes**.

## <a name="search-for-specific-threads"></a>Rechercher des threads spécifiques
 Vous pouvez rechercher des threads qui correspondent à une chaîne spécifiée dans le **Threads** fenêtre. Lorsque vous recherchez des threads, la fenêtre affiche tous les threads correspondant à la chaîne de recherche dans n’importe quelle colonne. Ces informations incluent l’emplacement de thread qui s’affiche en haut de la pile des appels dans la colonne **Emplacement**. Par défaut, la pile des appels complète n’est pas l’objet d’une recherche.

### <a name="to-search-for-specific-threads"></a>Pour rechercher des threads spécifiques

1. Dans la barre d’outils en haut de la fenêtre **Threads**, accédez à la zone **Rechercher** et effectuez l’une des opérations suivantes :

     - Entrez une chaîne de recherche, puis appuyez sur **entrée**.

     \- ou -

     - Sélectionnez la liste déroulante en regard du **recherche** zone, puis sélectionnez une chaîne de recherche à partir d’une recherche précédente.

2. (Facultatif) Pour inclure l’ensemble de la pile des appels dans la recherche, sélectionnez **Rechercher la pile des appels**.

## <a name="display-thread-call-stacks-and-switch-between-frames"></a>Afficher les piles d’appels de thread et basculer entre les images
Dans un programme multithread, chaque thread possède sa propre pile d'appel. La fenêtre **Threads** permet d’afficher facilement ces piles.

> [!TIP]
> Pour obtenir une représentation visuelle de la pile des appels pour chaque thread, utilisez la [piles parallèles](../debugger/get-started-debugging-multithreaded-apps.md) fenêtre.

### <a name="to-view-the-call-stack-of-a-thread"></a>Pour afficher la pile d'appel d'un thread

- Dans le **emplacement** colonne, sélectionnez le triangle inversé en regard de l’emplacement de thread.

     L’emplacement se développe pour indiquer la pile des appels du thread.

### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Pour afficher ou réduire les piles d‘appels de tous les threads

- Dans la barre d’outils en haut de la **Threads** fenêtre, sélectionnez **développer la pile des appels** ou **réduire la pile des appels**.

## <a name="see-also"></a>Voir aussi
- [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Bien démarrer avec le débogage d’applications multithread](../debugger/get-started-debugging-multithreaded-apps.md)
