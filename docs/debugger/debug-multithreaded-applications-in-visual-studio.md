---
title: "D&#233;boguer les applications multithread dans Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.gputthreads"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "déboguer (Visual Studio), calcul haute performance"
  - "déboguer (Visual Studio), multithread"
  - "débogage haute performance"
  - "débogage multithread"
  - "threads (Visual Studio), débogage"
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# D&#233;boguer les applications multithread dans Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un thread est une séquence d'instructions à laquelle le système d'exploitation alloue du temps processeur.  Chaque processus exécuté dans le système d'exploitation se compose d'au moins un thread.  Les processus qui comportent plusieurs threads sont appelés multithread.  
  
 Les ordinateurs avec plusieurs processeurs, des processeurs multicœur ou des processus d'hyperthreading peuvent exécuter plusieurs threads en même temps.  Le traitement en parallèle de plusieurs threads peut améliorer considérablement les performances du programme. Toutefois, il peut également compliquer le débogage, car il implique la nécessité de suivre plusieurs threads.  
  
 De plus, le multithreading introduit de nouveaux types de bogues potentiels.  Par exemple, plusieurs threads doivent souvent accéder à la même ressource, mais un seul thread peut accéder à la ressource en toute sécurité à un moment donné.  Une forme d'exclusion mutuelle est nécessaire pour s'assurer qu'un seul thread à la fois accède à la ressource.  Si l'exclusion mutuelle est exécutée de manière incorrecte, elle peut créer une condition d'*interblocage* dans laquelle aucun thread ne peut s'exécuter.  Le débogage des interblocages peut s'avérer particulièrement compliqué.  
  
 Visual Studio fournit une fenêtre **Threads**, une fenêtre Threads GPU, une fenêtre Espion parallèle et d'autres fonctionnalités permettant de faciliter le débogage multithread. Le meilleur moyen de se familiariser avec les fonctionnalités de threading consiste à suivre les procédures pas à pas.  Consultez [Procédure pas à pas : débogage d'une application multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md) et [Procédure pas\-à\-pas : débogage d’une application C\+\+ AMP](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md).  
  
 Visual Studio fournit également des points d'arrêt et des points de trace puissants, qui peuvent s'avérer très utiles lors du débogage d'applications multithread.  Vous pouvez utiliser des filtres de point d'arrêt pour placer des points d'arrêt sur des threads.  Consultez [Utilisation des points d'arrêt](../debugger/using-breakpoints.md).  
  
 Le débogage d'une application multithread comportant une interface utilisateur peut s'avérer tout particulièrement difficile.  Dans ce cas, vous pouvez envisager d'exécuter l'application sur un deuxième ordinateur et d'utiliser le débogage distant.  Pour plus d'informations, consultez [Débogage distant](../debugger/remote-debugging.md).  
  
## Dans cette section  
 [Déboguer les threads et processus](../debugger/debug-threads-and-processes.md)  
 Explique les concepts de base du débogage des threads et des processus.  
  
 [Déboguer les processus](../debugger/debug-multiple-processes.md)  
 Explique comment déboguer plusieurs processus.  
  
 [Comment : utiliser la fenêtre Threads](../debugger/how-to-use-the-threads-window.md)  
 Procédures utiles pour déboguer des threads à l'aide de la fenêtre **Threads**.  
  
 [Comment : basculer vers un autre thread pendant un débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Trois méthodes permettant de basculer le contexte de débogage vers un autre thread.  
  
 [Comment : ajouter et supprimer les indicateurs des threads](../Topic/How%20to:%20Flag%20and%20Unflag%20Threads.md)  
 Ajoutez des marques ou des indicateurs aux threads auxquels vous souhaitez prêter une attention particulière lors du débogage.  
  
 [Comment : définir un nom de thread dans le code natif](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Attribuez au thread un nom qui s'affiche dans la fenêtre **Threads**.  
  
 [Comment : définir un nom de thread dans le code managé](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Attribuez au thread un nom qui s'affiche dans la fenêtre **Threads**.  
  
 [Procédure pas à pas : débogage d'une application multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md).  
 Visite guidée des fonctionnalités de débogage de threads, qui insiste sur les fonctionnalités de [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
 [Comment : déboguer sur un cluster hautement performant](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Techniques permettant de déboguer une application exécutée sur un cluster hautement performant.  
  
 [Conseils pour le débogage de threads en code natif](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Techniques simples pouvant être utiles dans le cadre du débogage de threads natifs.  
  
 [Utilisation de la fenêtre Tâches](../debugger/using-the-tasks-window.md)  
 Affiche une liste de tous les objets de tâche managés ou natifs, en indiquant notamment leur état et d'autres informations utiles.  
  
 [Utilisation de la fenêtre Piles parallèles](../debugger/using-the-parallel-stacks-window.md)  
 Affiche les piles d'appels de plusieurs threads \(ou tâches\) dans une vue unique et fusionne également les segments de pile qui sont communs aux threads \(ou tâches\).  
  
 [Procédure pas à pas : débogage d'une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Procédure pas à pas qui indique comment utiliser les fenêtres Tâches parallèles et Piles parallèles.  
  
 [Comment : utiliser la fenêtre Espion parallèle](../debugger/how-to-use-the-parallel-watch-window.md)  
 Examinez les valeurs et les expressions entre plusieurs threads.  
  
 [Comment : utiliser la fenêtre Threads GPU](../Topic/How%20to:%20Use%20the%20GPU%20Threads%20Window.md)  
 Examinez et utilisez les threads qui s'exécutent sur le GPU pendant le débogage.  
  
## Rubriques connexes  
 [Utilisation des points d'arrêt](../debugger/using-breakpoints.md)  
 -   Utilisez des filtres de point d'arrêt pour placer un point d'arrêt sur un thread.  
  
-   Grâce aux points de trace, vous pouvez tracer l'exécution de votre programme sans interruption.  Cette fonction peut être utile pour étudier des problèmes tels que les interblocages.  
  
 [Threading](../Topic/Managed%20Threading.md)  
 Concepts de threading en programmation [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] avec exemple de code.  
  
 [Multithreading in Components](../Topic/Multithreading%20in%20Components.md)  
 Utilisation du multithreading dans les composants [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 [Prise en charge du multithreading pour le code plus ancien \(Visual C\+\+\)](/visual-cpp/parallel/multithreading/multithreading-support-for-older-code-visual-cpp)  
 Concepts de threading et exemple de code pour les programmeurs C\+\+ qui utilisent MFC.  
  
## Voir aussi  
 [Déboguer les threads et processus](../debugger/debug-threads-and-processes.md)   
 [Débogage distant](../debugger/remote-debugging.md)