---
title: Déboguer les applications multithread | Microsoft Docs
ms.custom: seodec18
ms.date: 11/06/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ea1af90ae775ed24f5cceabeca04cdc901f545f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059676"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Déboguer les applications multithread dans Visual Studio
Un thread est une séquence d’instructions à laquelle le système d’exploitation accorde le temps processeur. Chaque processus exécuté dans le système d'exploitation se compose d'au moins un thread. Les processus qui comportent plusieurs threads sont appelés multithread.  
  
Ordinateurs avec plusieurs processeurs, des processeurs multicœur ou des processus d’hyperthreading peuvent exécuter plusieurs threads simultanés. Traitement en parallèle à l’aide de nombreux threads peut améliorer considérablement les performances de programme, mais il peut également compliquer le débogage, car vous effectuez le suivi de threads.  
  
Le traitement multithread peut introduire de nouveaux types de bogues potentiels. Par exemple, deux ou plusieurs threads peut-être accéder à la même ressource, mais qu’un seul thread à la fois peut accéder en toute sécurité à la ressource. Une forme d’exclusion mutuelle est nécessaire pour s’assurer que seul un thread accède à la ressource à tout moment. Si l’exclusion mutuelle est implémentée correctement, il peut créer un *blocage* condition où aucun thread n’exécutera. Les interblocages sont souvent difficile à déboguer.

## <a name="tools-for-debugging-multithreaded-apps"></a>Outils de débogage d’applications multithreads

Visual Studio fournit différents outils pour une utilisation dans les applications multithread de débogage.

- Pour les threads, les principaux outils de débogage de threads sont les **Threads** fenêtre, les marqueurs de thread dans les fenêtres source le **piles parallèles** fenêtre, le **espion parallèle** fenêtre et le **emplacement de débogage** barre d’outils. Pour en savoir plus sur la **Threads** fenêtre et **emplacement de débogage** barre d’outils, consultez [procédure pas à pas : Déboguer à l’aide de la fenêtre Threads](../debugger/how-to-use-the-threads-window.md). Pour savoir comment utiliser le **piles parallèles** et **espion parallèle** windows, consultez [commencer le débogage d’une application multithread](../debugger/get-started-debugging-multithreaded-apps.md). Les deux rubriques montrent comment utiliser des marqueurs de thread.
  
- Pour le code qui utilise le [bibliothèque parallèle de tâches (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) ou le [Runtime d’accès concurrentiel](/cpp/parallel/concrt/concurrency-runtime/), les principaux outils de débogage sont le **piles parallèles** fenêtre, le **Espion parallèle** fenêtre et le **tâches** fenêtre, qui prend également en charge JavaScript. Pour commencer, consultez [procédure pas à pas : Débogage d’une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md) et [procédure pas à pas : Débogage d’une application C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application). 

- Pour déboguer des threads sur le GPU, le principal outil est la **Threads GPU** fenêtre. Consultez [Guide pratique pour utiliser la fenêtre Threads GPU](../debugger/how-to-use-the-gpu-threads-window.md).  

- Pour les processus, les principaux outils sont le **attacher au processus** boîte de dialogue, le **processus** fenêtre et le **emplacement de débogage** barre d’outils.  
  
Visual Studio fournit également des points d’arrêt puissants et des points de trace, qui peut être utile lorsque vous déboguez des applications multithread. Utiliser des conditions de point d’arrêt et de filtres pour placer des points d’arrêt sur des threads individuels. Points de trace vous permettent de suivre l’exécution de votre programme sans rupture pour étudier des problèmes tels que des blocages. Pour plus d’informations, consultez [actions de point d’arrêt et points de trace](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Le débogage d'une application multithread comportant une interface utilisateur peut s'avérer tout particulièrement difficile. Vous pouvez envisager l’application en cours d’exécution sur un deuxième ordinateur et l’utilisation du débogage à distance. Pour plus d’informations, consultez [le débogage à distance](../debugger/remote-debugging.md).  
  
## <a name="articles-about-debugging-multithreaded-apps"></a>Articles sur le débogage des applications multithreads

 [Commencer à déboguer une application multithread](../debugger/get-started-debugging-multithreaded-apps.md)   
 Visite guidée des fonctionnalités, en mettant l’accent sur les fonctionnalités dans débogage de threads le **piles parallèles** fenêtre et la **espion parallèle** fenêtre.

 [Outils de débogage de threads et processus](../debugger/debug-threads-and-processes.md)  
 Répertorie les fonctionnalités des outils pour le débogage des threads et processus.  
  
 [Déboguer plusieurs processus](../debugger/debug-multiple-processes.md)  
 Explique comment déboguer plusieurs processus.

 [Procédure pas à pas : Déboguer à l’aide de la fenêtre Threads](../debugger/how-to-use-the-threads-window.md).  
 Procédure pas à pas qui montre comment utiliser le **Threads** fenêtre et la **emplacement de débogage** barre d’outils. 

 [Procédure pas à pas : Déboguer une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Procédure pas à pas qui montre comment utiliser le **piles parallèles** et **tâches** windows.  
  
 [Guide pratique pour basculer vers un autre thread pendant un débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Plusieurs façons pour basculer le contexte de débogage vers un autre thread.  
  
 [Guide pratique pour ajouter et supprimer les indicateurs des threads](../debugger/how-to-flag-and-unflag-threads.md)  
 Ajoutez des marques ou des indicateurs aux threads auxquels vous souhaitez prêter une attention particulière lors du débogage.    
  
 [Guide pratique pour déboguer sur un cluster à hautes performances](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Techniques permettant de déboguer une application exécutée sur un cluster hautement performant.  

 [Conseils pour le débogage de threads en code natif](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Techniques simples pouvant être utiles dans le cadre du débogage de threads natifs. 

 [Guide pratique pour définir un nom de thread dans du code natif](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Attribuez au thread un nom qui s’affiche dans la fenêtre **Threads**.  
  
 [Guide pratique pour définir un nom de thread dans du code managé](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Attribuez au thread un nom qui s’affiche dans la fenêtre **Threads**. 
  
## <a name="see-also"></a>Voir aussi  

[Utiliser des points d’arrêt](../debugger/using-breakpoints.md)  
[Thread](/dotnet/standard/threading/index)  
[Multithreading dans les composants](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
[Prise en charge du multithreading pour le code plus ancien (Visual C++)](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)  
 [Déboguer les threads et les processus](../debugger/debug-threads-and-processes.md)   
 [Débogage distant](../debugger/remote-debugging.md)