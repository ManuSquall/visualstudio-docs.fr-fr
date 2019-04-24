---
title: Déboguer les applications multithread
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8315a797aec5fcedbf33df6ca96f41879b57d971
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054298"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Déboguer les applications multithread dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un thread est une séquence d'instructions à laquelle le système d'exploitation alloue du temps processeur. Chaque processus exécuté dans le système d'exploitation se compose d'au moins un thread. Les processus qui comportent plusieurs threads sont appelés multithread.

 Les ordinateurs avec plusieurs processeurs, des processeurs multicœur ou des processus d'hyperthreading peuvent exécuter plusieurs threads en même temps. Le traitement en parallèle de plusieurs threads peut améliorer considérablement les performances du programme. Toutefois, il peut également compliquer le débogage, car il implique la nécessité de suivre plusieurs threads.

 De plus, le multithreading introduit de nouveaux types de bogues potentiels. Par exemple, plusieurs threads doivent souvent accéder à la même ressource, mais un seul thread peut accéder à la ressource en toute sécurité à un moment donné. Une forme d'exclusion mutuelle est nécessaire pour s'assurer qu'un seul thread à la fois accède à la ressource. Si l’exclusion mutuelle est exécutée de manière incorrecte, elle peut créer un *blocage* condition dans laquelle aucun thread ne peut s’exécuter. Le débogage des interblocages peut s'avérer particulièrement compliqué.

 Visual Studio fournit un **Threads** fenêtre, une fenêtre Threads GPU, une fenêtre Espion parallèle et autres fonctionnalités de faciliter le débogage multithreads. Le meilleur moyen de se familiariser avec les fonctionnalités de threading consiste à suivre les procédures pas à pas. Consultez [Procédure pas à pas : Débogage d’une Application multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md) et [procédure pas à pas : Débogage d’une Application C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).

 Visual Studio fournit également des points d'arrêt et des points de trace puissants, qui peuvent s'avérer très utiles lors du débogage d'applications multithread. Vous pouvez utiliser des filtres de point d'arrêt pour placer des points d'arrêt sur des threads. Consultez [à l’aide de points d’arrêt](../debugger/using-breakpoints.md)

 Le débogage d'une application multithread comportant une interface utilisateur peut s'avérer tout particulièrement difficile. Dans ce cas, vous pouvez envisager d'exécuter l'application sur un deuxième ordinateur et d'utiliser le débogage distant. Pour plus d’informations, consultez [le débogage à distance](../debugger/remote-debugging.md).

## <a name="in-this-section"></a>Dans cette section
 [Déboguer les Threads et processus](../debugger/debug-threads-and-processes.md) explique les principes fondamentaux du débogage des threads et processus.

 [Déboguer plusieurs processus](../debugger/debug-multiple-processes.md) explique comment déboguer plusieurs processus.

 [Guide pratique pour Utiliser la fenêtre Threads](../debugger/how-to-use-the-threads-window.md) procédures utiles pour déboguer des threads avec le **Threads** fenêtre.

 [Guide pratique pour Basculer vers un autre Thread pendant le débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md) trois façons pour basculer le contexte de débogage vers un autre thread.

 [Guide pratique pour Indicateur et les Threads sans indicateur](../debugger/how-to-flag-and-unflag-threads.md) Mark ou indicateur de threads que vous souhaitez accorder une attention particulière lors du débogage.

 [Guide pratique pour Définir un nom de Thread en Code natif](../debugger/how-to-set-a-thread-name-in-native-code.md) attribuez au thread un nom qui s’affiche dans le **Threads** fenêtre.

 [Guide pratique pour Définir un nom de Thread dans du Code managé](../debugger/how-to-set-a-thread-name-in-managed-code.md) attribuez au thread un nom qui s’affiche dans le **Threads** fenêtre.

 [Procédure pas à pas : Débogage d’une Application multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md).
Visite guidée des fonctionnalités de débogage de threads, qui insiste sur les fonctionnalités de [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].

 [Guide pratique pour Déboguer sur un Cluster hautement performant](../debugger/how-to-debug-on-a-high-performance-cluster.md) Techniques de débogage d’une application qui s’exécute sur un cluster hautement performant.

 [Conseils pour le débogage de Threads en Code natif](../debugger/tips-for-debugging-threads-in-native-code.md) techniques simples qui peuvent être utiles pour le débogage de threads natifs.

 [À l’aide de la fenêtre tâches](../debugger/using-the-tasks-window.md) affiche une liste de tous les objets de tâche managés ou natifs, notamment leur état et autres informations utiles.

 [À l’aide de la fenêtre Piles parallèles](../debugger/using-the-parallel-stacks-window.md) appel affiche les piles de plusieurs threads (ou tâches) dans une vue unique et fusionne également les segments de pile qui sont communs aux threads (ou tâches).

 [Procédure pas à pas : Débogage d’une Application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md) procédure pas à pas qui montre comment utiliser les fenêtres tâches parallèles et piles parallèles.

 [Guide pratique pour Utiliser la fenêtre Espion parallèle](../debugger/how-to-use-the-parallel-watch-window.md) Inspecter les valeurs et les expressions entre plusieurs threads.

 [Guide pratique pour Utilisez la fenêtre Threads GPU](../debugger/how-to-use-the-gpu-threads-window.md) à examiner et manipuler des threads qui s’exécutent sur le GPU pendant le débogage.

## <a name="related-sections"></a>Rubriques connexes

[Utilisation des points d’arrêt](../debugger/using-breakpoints.md)
- Utilisez des filtres de point d'arrêt pour placer un point d'arrêt sur un thread.

- Grâce aux points de trace, vous pouvez tracer l'exécution de votre programme sans interruption. Cette fonction peut être utile pour étudier des problèmes tels que les interblocages.

  [Threading](http://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) concepts de Threading en [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] programmation, y compris des exemples de code.

  [Multithreading dans les composants](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) comment utiliser le multithreading dans [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] composants.

  [Prise en charge le multithreading pour le Code plus ancien (Visual C++)](http://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) concepts de Threading et exemple de code pour les programmeurs C++ à l’aide de MFC.

## <a name="see-also"></a>Voir aussi
 [Déboguer les Threads et processus](../debugger/debug-threads-and-processes.md) [le débogage à distance](../debugger/remote-debugging.md)
