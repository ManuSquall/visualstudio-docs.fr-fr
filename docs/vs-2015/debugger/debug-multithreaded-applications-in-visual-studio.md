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
ms.openlocfilehash: 8cb43c9a32f3dfd0a6383d466f7cd283acf0ab3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691281"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Déboguer les applications multithread dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un thread est une séquence d'instructions à laquelle le système d'exploitation alloue du temps processeur. Chaque processus exécuté dans le système d'exploitation se compose d'au moins un thread. Les processus qui comportent plusieurs threads sont appelés multithread.

 Les ordinateurs avec plusieurs processeurs, des processeurs multicœur ou des processus d'hyperthreading peuvent exécuter plusieurs threads en même temps. Le traitement en parallèle de plusieurs threads peut améliorer considérablement les performances du programme. Toutefois, il peut également compliquer le débogage, car il implique la nécessité de suivre plusieurs threads.

 De plus, le multithreading introduit de nouveaux types de bogues potentiels. Par exemple, plusieurs threads doivent souvent accéder à la même ressource, mais un seul thread peut accéder à la ressource en toute sécurité à un moment donné. Une forme d'exclusion mutuelle est nécessaire pour s'assurer qu'un seul thread à la fois accède à la ressource. Si l’exclusion mutuelle est exécutée de manière incorrecte, elle peut créer une condition de *blocage* dans laquelle aucun thread ne peut s’exécuter. Le débogage des interblocages peut s'avérer particulièrement compliqué.

 Visual Studio fournit une fenêtre **Threads** , une fenêtre threads GPU, une fenêtre Espion parallèle et d’autres fonctionnalités qui facilitent le débogage multithread. Le meilleur moyen de se familiariser avec les fonctionnalités de threading consiste à suivre les procédures pas à pas. Consultez [procédure pas à pas : débogage d’une application multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md) et [procédure pas à pas : débogage d’une application C++ amp](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).

 Visual Studio fournit également des points d'arrêt et des points de trace puissants, qui peuvent s'avérer très utiles lors du débogage d'applications multithread. Vous pouvez utiliser des filtres de point d'arrêt pour placer des points d'arrêt sur des threads. Voir [utilisation des points d’arrêt](../debugger/using-breakpoints.md)

 Le débogage d'une application multithread comportant une interface utilisateur peut s'avérer tout particulièrement difficile. Dans ce cas, vous pouvez envisager d'exécuter l'application sur un deuxième ordinateur et d'utiliser le débogage distant. Pour plus d’informations, consultez [débogage distant](../debugger/remote-debugging.md).

## <a name="in-this-section"></a>Dans cette section
 [Déboguer des threads et des processus](../debugger/debug-threads-and-processes.md) Explique les principes fondamentaux du débogage des threads et des processus.

 [Déboguer plusieurs processus](../debugger/debug-multiple-processes.md) Explique comment déboguer plusieurs processus.

 [Comment : utiliser la fenêtre threads](../debugger/how-to-use-the-threads-window.md) Procédures utiles pour déboguer des threads à l’aide de la fenêtre **Threads** .

 [Comment : basculer vers un autre thread pendant le débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md) Trois méthodes pour basculer le contexte de débogage vers un autre thread.

 [Comment : baliser et supprimer l’indicateur de threads](../debugger/how-to-flag-and-unflag-threads.md) Marquez ou signalez les threads auxquels vous souhaitez attirer une attention particulière lors du débogage.

 [Comment : définir un nom de thread dans du code natif](../debugger/how-to-set-a-thread-name-in-native-code.md) Donnez à votre thread un nom que vous affichez dans la fenêtre **Threads** .

 [Comment : définir un nom de thread dans du code managé](../debugger/how-to-set-a-thread-name-in-managed-code.md) Donnez à votre thread un nom que vous affichez dans la fenêtre **Threads** .

 [Procédure pas à pas : débogage d’une application multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md).
Visite guidée des fonctionnalités de débogage de threads, qui insiste sur les fonctionnalités de [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].

 [Procédure : déboguer sur un cluster à hautes performances](../debugger/how-to-debug-on-a-high-performance-cluster.md) Techniques permettant de déboguer une application qui s’exécute sur un cluster à hautes performances.

 [Conseils pour le débogage de threads en code natif](../debugger/tips-for-debugging-threads-in-native-code.md) Techniques simples qui peuvent être utiles pour déboguer des threads natifs.

 [Utilisation de la fenêtre tâches](../debugger/using-the-tasks-window.md) Affiche la liste de tous les objets de tâche managés ou natifs, y compris leur état et d’autres informations utiles.

 [Utilisation de la fenêtre piles parallèles](../debugger/using-the-parallel-stacks-window.md) Affiche les piles d’appels de plusieurs threads (ou tâches) dans une vue unique et fusionne également les segments de pile qui sont communs aux threads (ou tâches).

 [Procédure pas à pas : débogage d’une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md) Procédure pas à pas qui indique comment utiliser les fenêtres tâches parallèles et piles parallèles.

 [Comment : utiliser la fenêtre Espion parallèle](../debugger/how-to-use-the-parallel-watch-window.md) Inspectez les valeurs et les expressions entre plusieurs threads.

 [Comment : utiliser la fenêtre threads GPU](../debugger/how-to-use-the-gpu-threads-window.md) Examinez et utilisez les threads qui s’exécutent sur le GPU pendant le débogage.

## <a name="related-sections"></a>Sections connexes

[Utilisation des points d'arrêt](../debugger/using-breakpoints.md)
- Utilisez des filtres de point d'arrêt pour placer un point d'arrêt sur un thread.

- Grâce aux points de trace, vous pouvez tracer l'exécution de votre programme sans interruption. Cette fonction peut être utile pour étudier des problèmes tels que les interblocages.

  [Threads](https://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) Concepts de Threading en [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] programmation, y compris l’exemple de code.

  [Multithreading dans les composants](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) Comment utiliser le multithreading dans les [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] composants.

  [Prise en charge du multithreading pour le code plus ancien (Visual C++)](https://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) Concepts de Threading et exemple de code pour les programmeurs C++ utilisant MFC.

## <a name="see-also"></a>Voir aussi
 [Déboguer des threads et traiter](../debugger/debug-threads-and-processes.md) le [débogage distant](../debugger/remote-debugging.md)
