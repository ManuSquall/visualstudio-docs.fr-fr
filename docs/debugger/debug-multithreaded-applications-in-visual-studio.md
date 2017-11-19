---
title: "Déboguer les Applications multithread dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 09/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.gputthreads
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
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f8798616d9a39d46150f039ffe4340302439f31
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Déboguer les applications multithread dans Visual Studio
Un thread est une séquence d'instructions à laquelle le système d'exploitation alloue du temps processeur. Chaque processus exécuté dans le système d'exploitation se compose d'au moins un thread. Les processus qui comportent plusieurs threads sont appelés multithread.  
  
Les ordinateurs avec plusieurs processeurs, des processeurs multicœur ou des processus d'hyperthreading peuvent exécuter plusieurs threads en même temps. Le traitement en parallèle de plusieurs threads peut améliorer considérablement les performances du programme. Toutefois, il peut également compliquer le débogage, car il implique la nécessité de suivre plusieurs threads.  
  
De plus, le multithreading introduit de nouveaux types de bogues potentiels. Par exemple, plusieurs threads doivent souvent accéder à la même ressource, mais un seul thread peut accéder à la ressource en toute sécurité à un moment donné. Une forme d'exclusion mutuelle est nécessaire pour s'assurer qu'un seul thread à la fois accède à la ressource. Si l’exclusion mutuelle est exécutée de manière incorrecte, elle peut créer un *blocage* condition dans laquelle aucun thread ne peut s’exécuter. Le débogage des interblocages peut s'avérer particulièrement compliqué.

Visual Studio fournit différents outils à utiliser dans les applications multithreads de débogage.

- Pour les threads, les principaux outils de débogage de threads sont les **Threads** fenêtre, les marqueurs de thread dans les fenêtres source, **piles parallèles** fenêtre, **espion parallèle** fenêtre, et le **emplacement de débogage** barre d’outils. Pour en savoir plus sur les **Threads** fenêtre et **emplacement de débogage** barre d’outils, consultez [procédure pas à pas : déboguer à l’aide de la fenêtre Threads](../debugger/how-to-use-the-threads-window.md). Pour savoir comment utiliser le **piles parallèles** et **espion parallèle** windows, consultez [commencer à déboguer une application multithread](../debugger/get-started-debugging-multithreaded-apps.md). Les deux rubriques montrent comment utiliser des marqueurs de thread.
  
- Pour le code qui utilise le [bibliothèque parallèle de tâches (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) ou [Runtime d’accès concurrentiel](/cpp/parallel/concrt/concurrency-runtime/), les principaux outils de débogage sont la **piles parallèles** (fenêtre), la **Espion parallèle** fenêtre et la **tâches** fenêtre (la **tâches** fenêtre prend également en charge JavaScript). Pour commencer, consultez [procédure pas à pas : débogage d’une Application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md) et [procédure pas à pas : débogage d’une Application C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application.md). 

- Pour déboguer des threads sur le GPU, le principal outil est la **Threads GPU** fenêtre. Consultez [Comment : utiliser la fenêtre Threads GPU](../debugger/how-to-use-the-gpu-threads-window.md).  

- Pour les processus, les principaux outils sont le **attacher au processus** boîte de dialogue, la **processus** fenêtre et la **emplacement de débogage** barre d’outils.  
  
Visual Studio fournit également des points d'arrêt et des points de trace puissants, qui peuvent s'avérer très utiles lors du débogage d'applications multithread. Vous pouvez utiliser des conditions de point d’arrêt et de filtres pour placer des points d’arrêt sur des threads. Consultez [à l’aide de points d’arrêt](../debugger/using-breakpoints.md). 
  
Le débogage d'une application multithread comportant une interface utilisateur peut s'avérer tout particulièrement difficile. Dans ce cas, vous pouvez envisager d'exécuter l'application sur un deuxième ordinateur et d'utiliser le débogage distant. Pour plus d’informations, consultez [débogage distant](../debugger/remote-debugging.md).  
  
## <a name="in-this-section"></a>Dans cette section
 [Commencer à déboguer une application multithread](../debugger/get-started-debugging-multithreaded-apps.md).  
 Une visite guidée des fonctionnalités, qui insiste sur les fonctionnalités de débogage de threads le **piles parallèles** fenêtre et **espion parallèle** fenêtre.

 [Outils de débogage de Threads et processus](../debugger/debug-threads-and-processes.md)  
 Répertorie les fonctionnalités des outils pour le débogage des threads et processus.  
  
 [Déboguer plusieurs processus](../debugger/debug-multiple-processes.md)  
 Explique comment déboguer plusieurs processus.

 [Procédure pas à pas : Déboguer à l’aide de la fenêtre Threads](../debugger/how-to-use-the-threads-window.md).  
 Procédure pas à pas qui montre comment utiliser le **Threads** fenêtre et **emplacement de débogage** barre d’outils. 

 [Procédure pas à pas : Déboguer une Application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Procédure pas à pas qui montre comment utiliser le **piles parallèles** et **tâches** windows.  
  
 [Guide pratique pour basculer vers un autre thread pendant un débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Trois méthodes permettant de basculer le contexte de débogage vers un autre thread.  
  
 [Guide pratique pour ajouter et supprimer les indicateurs des threads](../debugger/how-to-flag-and-unflag-threads.md)  
 Ajoutez des marques ou des indicateurs aux threads auxquels vous souhaitez prêter une attention particulière lors du débogage.    
  
 [Guide pratique pour déboguer sur un cluster à hautes performances](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Techniques permettant de déboguer une application exécutée sur un cluster hautement performant.  

 [Conseils pour le débogage de threads en code natif](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Techniques simples pouvant être utiles dans le cadre du débogage de threads natifs. 

 [Guide pratique pour définir un nom de thread dans du code natif](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Attribuez au thread un nom qui s’affiche dans le **Threads** fenêtre.  
  
 [Guide pratique pour définir un nom de thread dans le code managé](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Attribuez au thread un nom qui s’affiche dans le **Threads** fenêtre. 
  
## <a name="related-sections"></a>Rubriques connexes  
 [Utilisation des points d’arrêt](../debugger/using-breakpoints.md)

 - Utiliser des conditions de point d’arrêt ou des filtres lorsque vous souhaitez déboguer un thread individuel.  
  
 - Grâce aux points de trace, vous pouvez tracer l'exécution de votre programme sans interruption. Cette fonction peut être utile pour étudier des problèmes tels que les interblocages.  
  
 [Thread](/dotnet/standard/threading/index)  
 Concepts de threading en programmation [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] avec exemple de code.  
  
 [Multithreading dans les composants](http://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
 Utilisation du multithreading dans les composants [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 [Prise en charge du multithreading pour le code plus ancien (Visual C++)](/cpp/parallel/multithreading/multithreading-support-for-older-code-visual-cpp)  
 Concepts de threading et exemple de code pour les programmeurs C++ qui utilisent MFC.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer les Threads et processus](../debugger/debug-threads-and-processes.md)   
 [Débogage à distance](../debugger/remote-debugging.md)