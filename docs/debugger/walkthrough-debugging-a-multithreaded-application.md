---
title: Afficher les threads dans le débogueur | Microsoft Docs
description: Utilisez des threads pour examiner et contrôler les threads. Vous pouvez regrouper, trier, marquer, figer, libérer et Rechercher des threads, sélectionner des colonnes et afficher des piles d’appels.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cd11e722886b77e9faaace768cc30a74c759903f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884206"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window-c-visual-basic-c"></a>Afficher les threads dans le débogueur Visual Studio à l’aide de la fenêtre threads (C#, Visual Basic, C++)
Dans la fenêtre **Threads** , vous pouvez examiner et utiliser des threads dans l’application que vous déboguez. Pour obtenir des instructions pas à pas sur l’utilisation de la fenêtre **Threads** , consultez [procédure pas à pas : déboguer à l’aide de la fenêtre threads](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>Utiliser la fenêtre Threads
 La fenêtre **Threads** contient une table dans laquelle chaque ligne décrit un thread distinct dans votre application. Par défaut, ce tableau répertorie tous les threads de votre application, mais vous pouvez filtrer la liste de façon à afficher uniquement les threads qui vous intéressent. Chaque colonne décrit un type d’informations différent. Vous pouvez également masquer certaines colonnes. Si vous affichez toutes les colonnes, les colonnes suivantes s’affichent, de gauche à droite :

- **Indicateur**: dans cette colonne sans étiquette, vous pouvez marquer un thread auquel vous souhaitez accorder une attention particulière. Pour plus d’informations sur la façon de marquer un thread, consultez [Comment : baliser et supprimer les indicateurs de threads](../debugger/how-to-flag-and-unflag-threads.md).

- **Thread actuel**: dans cette colonne sans étiquette, une flèche jaune indique le thread actuel. Un contour de flèche indique le contexte du débogueur actuel d’un thread non actuel.

- **ID**: affiche le numéro d’identification de chaque thread.

- **ID géré**: affiche les numéros d’identification managés des threads managés.

- **Catégorie**: affiche la catégorie de threads comme threads d’interface utilisateur, gestionnaires d’appel de procédure distante ou threads de travail. Une catégorie spéciale identifie le thread principal de l'application.

- **Nom**: identifie chaque thread par son nom, s’il en a un, ou comme \<No Name> .

- **Emplacement**: indique où le thread est en cours d’exécution. Vous pouvez développer cet emplacement de façon à afficher l’ensemble de la pile des appels du thread.

- **Priorité**: une colonne avancée (masquée par défaut) affiche la priorité ou précédence que le système a assignée à chaque thread.

- **Masque d’affinité**: une colonne avancée (masquée par défaut) indique le masque d’affinité de processeur pour chaque thread. Dans un système multiprocesseurs, le masque d'affinité détermine les processeurs sur lesquels un thread peut s'exécuter.

- **Compteur suspendu**: une colonne avancée (masquée par défaut) qui affiche le compteur suspendu. Ce compteur détermine si un thread peut s'exécuter. Pour plus d’informations sur les nombres suspendus, consultez [figer et libérer des threads](#freeze-and-thaw-threads).

- **Nom du processus**: une colonne avancée (masquée par défaut) affiche le processus auquel chaque thread appartient. Les données de cette colonne peuvent être utiles lorsque vous déboguez de nombreux processus.

- **ID de processus**: ID d’une colonne avancée (masquée par défaut) affiche le processus auquel chaque thread appartient.

- **Qualificateur de transport**: une colonne avancée (masquée par défaut) qui identifie de façon unique l’ordinateur auquel le débogueur est connecté.

### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Pour afficher la fenêtre Threads en mode arrêt ou en mode exécution

- Alors que Visual Studio est en mode débogage, sélectionnez le menu **Déboguer** , pointez sur **fenêtres**, puis sélectionnez **Threads**.

### <a name="to-display-or-hide-a-column"></a>Pour afficher ou masquer une colonne

- Dans la barre d’outils en haut de la fenêtre **Threads** , sélectionnez **colonnes**. Ensuite, activez ou désactivez le nom de la colonne que vous souhaitez afficher ou masquer.

## <a name="display-flagged-threads"></a>Afficher les threads avec indicateur
 Vous pouvez signaler un thread auquel vous souhaitez accorder une attention particulière en le marquant avec une icône dans la fenêtre **Threads**. Pour plus d’informations, consultez [Comment : baliser et supprimer les indicateurs de threads](../debugger/how-to-flag-and-unflag-threads.md). Dans la fenêtre **Threads** , vous pouvez choisir d’afficher tous les threads ou uniquement les threads avec indicateur.

### <a name="to-display-only-flagged-threads"></a>Pour afficher seulement les threads avec indicateur

- Choisissez **afficher les threads avec indicateur uniquement** dans la barre d’outils en haut de la fenêtre **Threads** . (S’il est grisé, vous devez d’abord marquer certains threads.)

## <a name="freeze-and-thaw-threads"></a>Figer et libérer des threads
 Lorsque vous gelez un thread, le système ne démarre pas l’exécution du thread même si des ressources sont disponibles.

 En code natif, vous pouvez interrompre ou reprendre des threads en appelant les fonctions Windows `SuspendThread` et `ResumeThread` . Ou appelez les fonctions MFC [CWinThread :: SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) et [CWinThread :: ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). Si vous appelez `SuspendThread` ou `ResumeThread` , le *nombre d’interruptions* affiché dans la fenêtre **Threads** sera modifié. Le compteur suspendu ne change pas si vous figez ou Libérez un thread natif. Un thread ne peut pas s’exécuter en code natif à moins qu’il ne soit libéré et qu’il ait un nombre suspendu de zéro.

 Dans le code managé, le nombre d’interruptions change lorsque vous figez ou Libérez un thread. Si vous figez un thread dans du code managé, son compteur suspendu est 1. Lorsque vous gelez un thread en code natif, son compteur suspendu est 0, sauf si vous avez utilisé l' `SuspendThread` appel.

> [!NOTE]
> Lors du débogage d'un appel entre code natif et code managé, le code managé s'exécute dans le même thread physique que le code natif qui l'a appelé. Si vous suspendez ou figez le thread natif, le code managé sera également figé.

### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Pour geler ou libérer l'exécution d'un thread

- Dans la barre d’outils en haut de la fenêtre **Threads** , sélectionnez **figer les threads** ou **libérer les threads**.

     Cette action affecte uniquement les threads sélectionnés dans la fenêtre **Threads**.

### <a name="switch-to-another-thread"></a>Basculer vers un autre thread

Une flèche jaune indique le thread actuel (et l’emplacement du pointeur d’exécution). Une flèche verte avec une queue d’extrémité indique qu’un thread non actuel a le contexte du débogueur actuel.

#### <a name="to-switch-to-another-thread"></a>Pour basculer vers un autre thread

- Suivez l’une des étapes suivantes :

  - Double-cliquez sur un thread.

  - Cliquez avec le bouton droit sur un thread, puis sélectionnez **basculer vers le thread**.

## <a name="group-and-sort-threads"></a>Threads de groupe et de tri
 Lorsque vous regroupez des threads, un titre s'affiche dans le tableau pour chaque groupe. L’en-tête contient une description de groupe, telle que **thread de travail** ou **threads non marqués**, ainsi qu’un contrôle d’arborescence. Les threads membres de chaque groupe apparaissent sous le titre approprié. Si vous souhaitez masquer les threads membres d’un groupe, utilisez le contrôle d’arborescence pour réduire le groupe.

 Étant donné que le regroupement est prioritaire sur le tri, vous pouvez grouper des threads par catégorie, par exemple, puis les trier par ID dans chaque catégorie.

### <a name="to-sort-threads"></a>Pour trier des threads

1. Dans la barre d’outils en haut de la fenêtre **Threads** , sélectionnez le bouton en haut de toute colonne.

     Les threads sont alors triés en fonction des valeurs de la colonne choisie.

2. Si vous souhaitez inverser l’ordre de tri, sélectionnez de nouveau le même bouton.

     Les threads qui figuraient au début de la liste s'affichent maintenant à la fin.

### <a name="to-group-threads"></a>Pour regrouper des threads

- Dans la barre d’outils de la fenêtre **Threads** , sélectionnez la liste **regrouper par** , puis sélectionnez les critères par lesquels vous souhaitez regrouper les threads.

### <a name="to-sort-threads-within-groups"></a>Pour trier des threads au sein de groupes

1. Dans la barre d’outils en haut de la fenêtre **Threads** , sélectionnez la liste **regrouper par** , puis sélectionnez les critères par lesquels vous souhaitez regrouper les threads.

2. Dans la fenêtre **Threads** , sélectionnez le bouton situé en haut de toute colonne.

     Les threads sont alors triés en fonction des valeurs de la colonne choisie.

### <a name="to-expand-or-collapse-all-groups"></a>Pour développer ou réduire tous les groupes

- Dans la barre d’outils en haut de la fenêtre **Threads** , sélectionnez **développer les groupes** ou **réduire les groupes**.

## <a name="search-for-specific-threads"></a>Rechercher des threads spécifiques
 Vous pouvez rechercher des threads qui correspondent à une chaîne spécifiée dans la fenêtre **Threads** . Lorsque vous recherchez des threads, la fenêtre affiche tous les threads qui correspondent à la chaîne recherchée dans n’importe quelle colonne. Ces informations incluent l’emplacement de thread qui s’affiche en haut de la pile des appels dans la colonne **Emplacement**. Par défaut, la pile des appels complète n’est pas recherchée.

### <a name="to-search-for-specific-threads"></a>Pour rechercher des threads spécifiques

1. Dans la barre d’outils en haut de la fenêtre **Threads**, accédez à la zone **Rechercher** et effectuez l’une des opérations suivantes :

     - Entrez une chaîne de recherche, puis appuyez sur **entrée**.

     \- ou -

     - Sélectionnez la liste déroulante en regard de la zone de **recherche** et sélectionnez une chaîne de recherche à partir d’une recherche précédente.

2. (Facultatif) Pour inclure l’ensemble de la pile des appels dans la recherche, sélectionnez **Rechercher la pile des appels**.

## <a name="display-thread-call-stacks-and-switch-between-frames"></a>Afficher les piles d’appels des threads et basculer entre les frames
Dans un programme multithread, chaque thread possède sa propre pile d'appel. La fenêtre **Threads** permet d’afficher facilement ces piles.

> [!TIP]
> Pour obtenir une représentation visuelle de la pile des appels pour chaque thread, utilisez la fenêtre [Piles parallèles](../debugger/get-started-debugging-multithreaded-apps.md) .

### <a name="to-view-the-call-stack-of-a-thread"></a>Pour afficher la pile d'appel d'un thread

- Dans la colonne **emplacement** , sélectionnez le triangle inversé en regard de l’emplacement du thread.

     L'emplacement se développe pour indiquer la pile des appels du thread.

### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Pour afficher ou réduire les piles d‘appels de tous les threads

- Dans la barre d’outils en haut de la fenêtre **Threads** , sélectionnez **développer les piles des appels** ou réduire les piles d' **appels**.

## <a name="see-also"></a>Voir aussi
- [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Bien démarrer avec le débogage d’applications multithreads](../debugger/get-started-debugging-multithreaded-apps.md)
