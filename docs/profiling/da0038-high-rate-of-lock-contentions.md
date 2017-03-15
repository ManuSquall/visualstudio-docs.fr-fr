---
title: "DA0038&#160;: taux &#233;lev&#233; de conflits de verrouillage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.38"
  - "vs.performance.rules.DA0038"
  - "vs.performance.DA0038"
ms.assetid: ae0c8b2f-17b2-4f3d-a834-aa2f6371753b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# DA0038&#160;: taux &#233;lev&#233; de conflits de verrouillage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0038|  
|Catégorie|Utilisation du .NET Framework|  
|Méthode de profilage|Échantillonnage<br /><br /> Instrumentation<br /><br /> Mémoire .NET|  
|Message|Un taux très élevé de conflits de verrou .NET se produit.  Analysez la raison de ce conflit de verrou en exécutant un profil Concurrence.|  
|Type de règle|Information|  
  
 Lorsque vous profilez en utilisant les méthodes d'échantillonnage, de mémoire. NET ou de conflits de ressources, vous devez collecter au moins 25 échantillons pour déclencher cette règle.  
  
## Cause  
 Les données des performances système collectées avec les données de profilage indiquent qu'un taux considérablement élevé de conflits de verrouillage a été relevé pendant l'exécution de l'application.  Envisagez un autre profilage à l'aide de la méthode de profilage d'accès concurrentiel pour découvrir la cause des conflits.  
  
## Description de la règle  
 Les verrous sont utilisés pour protéger des sections critiques de code qui doit être exécuté de façon séquentielle par un seul thread à la fois dans une application multithread.  Le CLR \(Common Language Runtime\) de Microsoft .NET fournit un jeu complet de primitives de synchronisation et de verrouillage.  Par exemple, le langage C\# prend en charge une instruction lock \(SyncLock en Visual Basic\).  Une application managée peut appeler les méthodes Monitor.Enter et Monitor.Exit dans l'espace de noms System.Threading pour acquérir et libérer un verrou directement.  Le .NET Framework prend en charge des primitives de synchronisation et de verrouillage supplémentaires, notamment les classes qui prennent en charge Mutexes, ReaderWriterLocks et Semaphores.  Pour plus d'informations, consultez [Vue d'ensemble des primitives de synchronisation](http://go.microsoft.com/fwlink/?LinkId=177867) dans le Guide du développeur .NET Framework sur le site Web MSDN.  Les classes .NET Framework sont elles\-mêmes superposées sur les services de synchronisation du niveau inférieur intégrés au système d'exploitation Windows.  Sont inclus des objets de section critiques et de nombreuses fonctions d'attente et de signalement d'événement.  Pour plus d'informations, consultez [Synchronisation](http://go.microsoft.com/fwlink/?LinkId=177869) la section de développement de Win32 et COM dans la bibliothèque MSDN  
  
 Les classes .NET Framework sous\-jacentes et les objets Windows natifs sous\-jacents utilisés pour la synchronisation et le verrouillage représentent des emplacements de mémoire partagée qui doivent être modifiés à l'aide d'opérations verrouillées.  Les opérations verrouillées utilisent des instructions spécifiques au matériel qui fonctionnent dans les emplacements de mémoire partagée pour modifier leur état à l'aide d'opérations atomiques.  La cohérence des opérations atomiques est garantie entre tous les processeurs de l'ordinateur.  Locks et WaitHandles sont des objets .NET qui utilisent automatiquement les opérations verrouillées lorsqu'ils sont définis ou réinitialisés.  Il peut exister d'autres structures de données de mémoire partagée dans votre application qui requièrent également que vous utilisiez des opérations verrouillées pour permettre une mise à jour thread\-safe.  Pour plus d'informations, consultez [Opérations enclenchées](http://go.microsoft.com/fwlink/?LinkId=177870) dans la section du .NET Framework de la bibliothèque de MSND  
  
 La synchronisation et le verrouillage sont des mécanismes permettant de s'assurer que les applications de multithreading s'exécutent correctement.  Chaque thread d'une application multithread est une unité d'exécution indépendante qui est planifiée indépendamment par le système d'exploitation.  Des conflits de verrouillage se produisent chaque fois qu'un thread qui essaie d'acquérir un verrou est retardé parce qu'un autre thread détient le verrou.  
  
 Les verrous sont fréquemment imbriqués.  L'imbrication se produit lorsqu'un thread qui exécute une section critique lance une fonction qui requiert ensuite un autre verrou.  Une certaine quantité d'imbrication de verrous est inévitable.  Votre section critique peut appeler une méthode .NET Framework basée sur les verrous pour vérifier sa nature thread\-safe.  Un appel provenant d'une section critique de votre application dans une méthode Framework qui verrouille également à l'aide d'un handle de verrou différent provoque l'imbrication des verrous.  Les conditions de verrouillage imbriqué peuvent entraîner des problèmes de performances notoirement difficiles à démêler et à résoudre.  
  
 Cette règle se déclenche lorsque les mesures prises pendant une exécution de profilage indiquent une quantité excessivement élevée de conflit de verrouillage.  Les conflits de verrouillage diffèrent l'exécution des threads qui attendent le verrou.  Même d'assez petites quantités de conflits de verrouillage dans les tests unitaires ou tests de charge exécutés sur un matériel bas de gamme doivent être examinées.  
  
> [!NOTE]
>  Lorsque le taux de conflits de verrouillage signalés dans les données de profilage est extrêmement élevé, c'est le message d'avertissement [DA0039 : taux très élevé de conflits de verrouillage](../profiling/da0039-very-high-rate-of-lock-contentions.md) qui est déclenché à la place de ce message d'information.  
  
## Comment examiner un avertissement  
 Double\-cliquez sur le message pour naviguer jusqu'à l'affichage [Marques](../profiling/marks-view.md) des données de profilage.  Recherchez la colonne **Verrous et threads CLR .NET\\Taux de conflits\/s**.  Déterminez s'il existe des phases spécifiques de l'exécution du programme où les conflits de verrouillage sont plus importants que dans d'autres phases.  
  
 Cette règle se déclenche uniquement lorsque vous n'utilisez pas la méthode de profilage d'accès concurrentiel.  La méthode de profilage d'accès concurrentiel constitue le meilleur outil pour diagnostiquer les problèmes de performances liés au conflit de verrouillage dans votre application.  Collectez des données de profilage d'accès concurrentiel pour comprendre le comportement de verrouillage de votre application.  Cela permet de comprendre quels verrous génèrent le plus grand nombre de conflits, combien de temps l'exécution de thread est différée pour les verrous affectés par des conflits et quel code spécifique est impliqué.  Les profils d'accès concurrentiel collectent des données sur tous les conflits de verrouillage, y compris le comportement de verrouillage des installations Windows natives, des classes .NET Framework et de toute autre bibliothèque tierce que votre application référence.  Pour plus d'informations sur le profilage d'accès concurrentiel à partir de l'IDE [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consultez [Collecte de données de concurrence de threads et de processus](../profiling/collecting-thread-and-process-concurrency-data.md).  Pour obtenir des liens vers des informations sur le profilage d'accès concurrentiel à partir de la ligne de commande, consultez la section **Using the Concurrency Method to Collect Resource Contention and Thread Activity Data** de [Utilisation de méthodes de profilage à partir de la ligne de commande](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).