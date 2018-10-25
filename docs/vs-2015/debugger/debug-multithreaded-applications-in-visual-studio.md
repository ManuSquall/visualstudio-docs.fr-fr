---
title: Déboguer les Applications multithread dans Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d841456ab95d06a7b586f7a8566f8530acbb021
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897496"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Déboguer les applications multithread dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un thread est une séquence d'instructions à laquelle le système d'exploitation alloue du temps processeur. Chaque processus exécuté dans le système d'exploitation se compose d'au moins un thread. Les processus qui comportent plusieurs threads sont appelés multithread.  
  
 Les ordinateurs avec plusieurs processeurs, des processeurs multicœur ou des processus d'hyperthreading peuvent exécuter plusieurs threads en même temps. Le traitement en parallèle de plusieurs threads peut améliorer considérablement les performances du programme. Toutefois, il peut également compliquer le débogage, car il implique la nécessité de suivre plusieurs threads.  
  
 De plus, le multithreading introduit de nouveaux types de bogues potentiels. Par exemple, plusieurs threads doivent souvent accéder à la même ressource, mais un seul thread peut accéder à la ressource en toute sécurité à un moment donné. Une forme d'exclusion mutuelle est nécessaire pour s'assurer qu'un seul thread à la fois accède à la ressource. Si l’exclusion mutuelle est exécutée de manière incorrecte, elle peut créer un *blocage* condition dans laquelle aucun thread ne peut s’exécuter. Le débogage des interblocages peut s'avérer particulièrement compliqué.  
  
 Visual Studio fournit un **Threads** fenêtre, une fenêtre Threads GPU, une fenêtre Espion parallèle et autres fonctionnalités de faciliter le débogage multithreads. Le meilleur moyen de se familiariser avec les fonctionnalités de threading consiste à suivre les procédures pas à pas. Consultez [procédure pas à pas : débogage d’une Application multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md) et [procédure pas à pas : débogage d’une Application C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).  
  
 Visual Studio fournit également des points d'arrêt et des points de trace puissants, qui peuvent s'avérer très utiles lors du débogage d'applications multithread. Vous pouvez utiliser des filtres de point d'arrêt pour placer des points d'arrêt sur des threads. Consultez [à l’aide de points d’arrêt](../debugger/using-breakpoints.md)  
  
 Le débogage d'une application multithread comportant une interface utilisateur peut s'avérer tout particulièrement difficile. Dans ce cas, vous pouvez envisager d'exécuter l'application sur un deuxième ordinateur et d'utiliser le débogage distant. Pour plus d’informations, consultez [le débogage à distance](../debugger/remote-debugging.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Déboguer les threads et les processus](../debugger/debug-threads-and-processes.md)  
 Explique les concepts de base du débogage des threads et des processus.  
  
 [Déboguer plusieurs processus](../debugger/debug-multiple-processes.md)  
 Explique comment déboguer plusieurs processus.  
  
 [Guide pratique pour utiliser la fenêtre Threads](../debugger/how-to-use-the-threads-window.md)  
 Procédures utiles pour déboguer des threads avec le **Threads** fenêtre.  
  
 [Guide pratique pour basculer vers un autre thread pendant un débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Trois méthodes permettant de basculer le contexte de débogage vers un autre thread.  
  
 [Guide pratique pour ajouter et supprimer les indicateurs des threads](../debugger/how-to-flag-and-unflag-threads.md)  
 Ajoutez des marques ou des indicateurs aux threads auxquels vous souhaitez prêter une attention particulière lors du débogage.  
  
 [Guide pratique pour définir un nom de thread dans du code natif](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Attribuez au thread un nom qui s’affiche dans le **Threads** fenêtre.  
  
 [Guide pratique pour définir un nom de thread dans le code managé](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Attribuez au thread un nom qui s’affiche dans le **Threads** fenêtre.  
  
 [Procédure pas à pas : Débogage d’une Application multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md).  
 Visite guidée des fonctionnalités de débogage de threads, qui insiste sur les fonctionnalités de [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].  
  
 [Guide pratique pour déboguer sur un cluster à hautes performances](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Techniques permettant de déboguer une application exécutée sur un cluster hautement performant.  
  
 [Conseils pour le débogage de threads en code natif](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Techniques simples pouvant être utiles dans le cadre du débogage de threads natifs.  
  
 [Utilisation de la fenêtre Tâches](../debugger/using-the-tasks-window.md)  
 Affiche une liste de tous les objets de tâche managés ou natifs, en indiquant notamment leur état et d’autres informations utiles.  
  
 [Utilisation de la fenêtre Piles parallèles](../debugger/using-the-parallel-stacks-window.md)  
 Affiche les piles d’appels de plusieurs threads (ou tâches) dans une vue unique et fusionne également les segments de pile qui sont communs aux threads (ou tâches).  
  
 [Procédure pas à pas : débogage d’une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Procédure pas à pas qui indique comment utiliser les fenêtres Tâches parallèles et Piles parallèles.  
  
 [Guide pratique pour utiliser la fenêtre Espion parallèle](../debugger/how-to-use-the-parallel-watch-window.md)  
 Examinez les valeurs et les expressions entre plusieurs threads.  
  
 [Guide pratique pour utiliser la fenêtre Threads GPU](../debugger/how-to-use-the-gpu-threads-window.md)  
 Examinez et utilisez les threads qui s'exécutent sur le GPU pendant le débogage.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Utilisation des points d’arrêt](../debugger/using-breakpoints.md)  
 -   Utilisez des filtres de point d'arrêt pour placer un point d'arrêt sur un thread.  
  
- Grâce aux points de trace, vous pouvez tracer l'exécution de votre programme sans interruption. Cette fonction peut être utile pour étudier des problèmes tels que les interblocages.  
  
  [Thread](http://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87)  
  Concepts de threading en programmation [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] avec exemple de code.  
  
  [Multithreading dans les composants](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
  Utilisation du multithreading dans les composants [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
  [Prise en charge du multithreading pour le code plus ancien (Visual C++)](http://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c)  
  Concepts de threading et exemple de code pour les programmeurs C++ qui utilisent MFC.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer les Threads et processus](../debugger/debug-threads-and-processes.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



