---
title: Déboguer des applications multithread | Microsoft Docs
ms.custom: seodec18
ms.date: 11/06/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 668e95c340348eeb1fa509622aa44d99b65b6efc
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72431807"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Déboguer les applications multithread dans Visual Studio
Un thread est une séquence d’instructions à laquelle le système d’exploitation accorde du temps processeur. Chaque processus exécuté dans le système d'exploitation se compose d'au moins un thread. Les processus qui comportent plusieurs threads sont appelés multithread.

Les ordinateurs équipés de plusieurs processeurs, des processeurs multicœur ou des processus d’hyperthreading peuvent exécuter plusieurs threads simultanés. Le traitement parallèle à l’aide de nombreux threads peut améliorer les performances du programme, mais il peut également compliquer le débogage, car vous effectuez le suivi de nombreux threads.

Le multithreading peut introduire de nouveaux types de bogues potentiels. Par exemple, deux threads ou plus peuvent avoir besoin d’accéder à la même ressource, mais un seul thread à la fois peut accéder en toute sécurité à la ressource. Une certaine forme d’exclusion mutuelle est nécessaire pour s’assurer qu’un seul thread accède à la ressource à tout moment. Si l’exclusion mutuelle est implémentée de manière incorrecte, elle peut créer une condition de *blocage* dans laquelle aucun thread ne s’exécutera. Les blocages sont souvent un problème difficile à déboguer.

## <a name="tools-for-debugging-multithreaded-apps"></a>Outils de débogage d’applications multithread

Visual Studio fournit différents outils à utiliser pour déboguer des applications multithread.

- Pour les threads, les principaux outils de débogage des threads sont la fenêtre **Threads** , les marqueurs de thread dans les fenêtres source, la fenêtre **Piles parallèles** , la fenêtre **Espion parallèle** et la barre d’outils **emplacement de débogage** . Pour en savoir plus sur la **Threads** fenêtre et **emplacement de débogage** barre d’outils, consultez [procédure pas à pas : Déboguer à l’aide de la fenêtre Threads](../debugger/how-to-use-the-threads-window.md). Pour savoir comment utiliser les **Piles parallèles** et les fenêtres **Espion parallèle** , consultez [prise en main du débogage d’une application multithread](../debugger/get-started-debugging-multithreaded-apps.md). Les deux rubriques montrent comment utiliser des marqueurs de thread.

- Pour le code qui utilise la [bibliothèque parallèle de tâches (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) ou la [Runtime d’accès concurrentiel](/cpp/parallel/concrt/concurrency-runtime/), les principaux outils de débogage sont la fenêtre **Piles parallèles** , la fenêtre **Espion parallèle** et la fenêtre **tâches** , qui prend également en charge JavaScript. Pour commencer, consultez [procédure pas à pas : débogage d’une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md) et [procédure pas à pas C++ : débogage d’une application amp](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application).

- Pour déboguer des threads sur le GPU, l’outil principal est la fenêtre **Threads GPU** . Consultez [Comment : utiliser la fenêtre threads GPU](../debugger/how-to-use-the-gpu-threads-window.md).

- Pour les processus, les outils principaux sont la boîte de dialogue **attacher au processus** , la fenêtre **processus** et la barre d’outils **emplacement de débogage** .

Visual Studio fournit également des points d’arrêt et des points de trace puissants, qui peuvent être utiles quand vous déboguez des applications multithread. Utilisez des conditions de point d’arrêt et des filtres pour placer des points d’arrêt sur des threads individuels. Les points de trace vous permettent de suivre l’exécution de votre programme sans interruption, afin d’étudier des problèmes tels que les blocages. Pour plus d’informations, consultez [actions de point d’arrêt et points de trace](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Le débogage d'une application multithread comportant une interface utilisateur peut s'avérer tout particulièrement difficile. Vous pouvez envisager d’exécuter l’application sur un deuxième ordinateur et d’utiliser le débogage distant. Pour plus d’informations, consultez [débogage distant](../debugger/remote-debugging.md).

## <a name="articles-about-debugging-multithreaded-apps"></a>Articles sur le débogage d’applications multithread

 [Prise en main du débogage d’une application multithread](../debugger/get-started-debugging-multithreaded-apps.md)

Visite guidée des fonctionnalités de débogage des threads, en soulignant les fonctionnalités de la fenêtre **Piles parallèles** et de la fenêtre **Espion parallèle** .

 [Outils de débogage de threads et de processus](../debugger/debug-threads-and-processes.md)

Répertorie les fonctionnalités des outils de débogage des threads et des processus.

 [Déboguer plusieurs processus](../debugger/debug-multiple-processes.md)

Explique comment déboguer plusieurs processus.

 [Procédure pas à pas : déboguer à l’aide de la fenêtre Threads](../debugger/how-to-use-the-threads-window.md).

Procédure pas à pas qui indique comment utiliser la fenêtre **Threads** et la barre d’outils **emplacement de débogage** .

 [Procédure pas à pas : déboguer une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md)

Procédure pas à pas qui indique comment utiliser les fenêtres **Piles parallèles** et **tâches** .

 [Guide pratique pour basculer vers un autre thread pendant un débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md)

Plusieurs méthodes pour basculer le contexte de débogage vers un autre thread.

 [Guide pratique pour ajouter et supprimer des threads](../debugger/how-to-flag-and-unflag-threads.md)

Ajoutez des marques ou des indicateurs aux threads auxquels vous souhaitez prêter une attention particulière lors du débogage.

 [Guide pratique pour déboguer sur un cluster hautement performant](../debugger/how-to-debug-on-a-high-performance-cluster.md)

Techniques permettant de déboguer une application exécutée sur un cluster hautement performant.

 [Conseils pour le débogage de threads en code natif](../debugger/tips-for-debugging-threads-in-native-code.md)

Techniques simples pouvant être utiles dans le cadre du débogage de threads natifs.

 [Guide pratique pour définir un nom de thread dans du code natif](../debugger/how-to-set-a-thread-name-in-native-code.md)

Attribuez au thread un nom qui s’affiche dans la fenêtre **Threads**.

 [Guide pratique pour définir un nom de thread dans du code managé](../debugger/how-to-set-a-thread-name-in-managed-code.md)

Attribuez au thread un nom qui s’affiche dans la fenêtre **Threads**.

## <a name="see-also"></a>Voir aussi

- [Utiliser des points d’arrêt](../debugger/using-breakpoints.md)
- [Thread](/dotnet/standard/threading/index)
- [Multithreading dans les composants](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)
- [Prise en charge du multithreading pour le code plus ancien](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [Déboguer les threads et processus](../debugger/debug-threads-and-processes.md)
- [Débogage à distance](../debugger/remote-debugging.md)