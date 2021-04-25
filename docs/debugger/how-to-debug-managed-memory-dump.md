---
title: Déboguer une image mémoire managée avec des analyseurs de diagnostic .NET | Microsoft Docs
description: Découvrez comment utiliser les analyseurs de diagnostic .NET de Visual Studio pour analyser une image mémoire managée
ms.custom: SEO-VS-2021
ms.date: 04/21/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- analyzers
- dump debugging
- debugging managed memory dump
- debugging [Visual Studio]
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 083095ad534aa6b9131ba103178313cb1cdc4b7c
ms.sourcegitcommit: 925db7adb9cb554b081c7e727d09680d4863feed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2021
ms.locfileid: "107952900"
---
# <a name="how-to-debug-a-managed-memory-dump-with-net-diagnostic-analyzers"></a>Comment déboguer une image mémoire managée avec des analyseurs de diagnostic .NET



Ce didacticiel présente les procédures suivantes :

> [!div class="checklist"]
> * Ouverture d’un vidage de la mémoire
> * Sélectionner et exécuter des analyseurs sur le dump
> * Examiner les résultats des analyseurs
> * Naviguer jusqu’au code problématique


Dans l’exemple décrit dans cet article, le problème est que votre application ne répond pas aux demandes en temps opportun. 


## <a name="opening-a-memory-dump-in-visual-studio"></a>Ouverture d’un vidage de la mémoire dans Visual Studio

1. Ouvrez le vidage de la mémoire dans Visual Studio à l’aide de la commande de menu **fichier > ouvrir > fichier** , puis sélectionnez votre image mémoire.

1. Notez dans la page Résumé de vidage de la mémoire une nouvelle **action** appelée **exécuter l’analyse des diagnostics**.

   ![Action-analyse des diagnostics](../debugger/media/diagnostic-analyzer-dump-summary-actions.png)

1. Sélectionnez cette action pour démarrer le débogueur et ouvrir la nouvelle page **analyse de diagnostic** avec une liste des options d’analyseur disponibles, organisée par le symptôme sous-jacent.


## <a name="select-and-execute-analyzers-against-the-dump"></a>Sélectionner et exécuter des analyseurs sur le dump

Pour examiner ces symptômes, les meilleures options sont disponibles sous **réactivité du processus** , car il correspond le mieux au problème dans cet exemple.

   ![Sélectionner des analyseurs de diagnostic](../debugger/media/diagnostic-analyzer-diagnostics-analysis-window.png)

1. Cliquez sur le bouton **analyser** pour démarrer le processus d’investigation. 

1. L’analyseur présente des résultats en fonction de la combinaison d’informations de processus et de données CLR capturées dans l’image mémoire.
 
## <a name="review-the-results-of-the-analyzers"></a>Examiner les résultats des analyseurs

1. Dans ce cas, l’analyseur a trouvé deux erreurs. Sélectionnez le résultat de l’analyseur pour afficher le résumé de l' **analyse** et la **Correction** suggérée.

   ![Résultats des analyseurs de diagnostic](../debugger/media/diagnostic-analyzer-diagnostics-analysis-results.png)

1. Le **Résumé** de l’analyse a déclaré que le « pool de threads CLR subit une insuffisance ». Ces informations suggèrent que le CLR a actuellement utilisé tous les threads de pool de threads disponibles, ce qui signifie que votre service ne peut répondre à aucune nouvelle demande tant qu’un thread n’est pas libéré.

    > [!NOTE] 
    > Dans ce cas, la mise à **jour** est «ne pas attendre de manière synchrone les analyses, événements, tâches ou tout autre objet susceptible de bloquer votre thread. Vérifiez si vous pouvez mettre à jour la méthode pour qu’elle soit asynchrone.».

## <a name="navigating-to-the-problematic-code"></a>Naviguer jusqu’au code problématique

Mon prochain travail est de trouver ce code problématique.

1. En cliquant sur le lien **afficher la pile des appels** , Visual Studio bascule immédiatement vers les threads qui présentent ce comportement.

1. La fenêtre **pile des appels** affiche les méthodes qui peuvent potentiellement faire une distinction rapide entre mon code (SyncOverAsyncExmple.) et le *Code de l’infrastructure (System.*).

   ![Liens des analyseurs de diagnostic vers la pile des appels](../debugger/media/diagnostic-analyzer-call-stack.png)

1. Chaque frame de pile des appels correspond à une méthode et le fait de double-cliquer sur les frames de pile permet à Visual Studio d’accéder au code qui a conduit directement à ce scénario sur ce thread.

1. Dans cet exemple, il n’y a aucun symbole ou code, toutefois, sur la page **symboles non chargés** , vous pouvez sélectionner l’option **[décompiler le code source](../debugger/decompilation.md)** .

   ![Décompilation](../debugger/media/diagnostic-analyzer-decompilation.png)

1. Dans la source décompilée ci-dessous, il est évident qu’une tâche asynchrone (ConsumeThreadPoolThread) appelle une fonction de blocage synchrone.

    > [!NOTE]  
    > Méthode « DoSomething () » qui contient une méthode WaitHandle. WaitOne qui bloque le thread du pool de threads actuel jusqu’à ce qu’il reçoive un signal.

   Pour améliorer la réactivité des applications, il est important de supprimer le blocage du code synchrone de tous les contextes asynchrones.

   ![Analyser le code décompilé](../debugger/media/diagnostic-analyzer-decompiled-code.png)


## <a name="see-also"></a>Voir aussi

* [Utiliser des fichiers dump dans le débogueur](../debugger/using-dump-files.md)
* [Générer du code source à partir d’assemblys .NET pendant le débogage](../debugger/decompilation.md)
* [Spécifier les fichiers de symboles (. pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
