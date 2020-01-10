---
title: 'DA0038 : Taux élevé de conflits de verrou | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.38
- vs.performance.rules.DA0038
- vs.performance.DA0038
ms.assetid: ae0c8b2f-17b2-4f3d-a834-aa2f6371753b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28a2998f1521c612823ee59dcfe8484f2213e026
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850932"
---
# <a name="da0038-high-rate-of-lock-contentions"></a>DA0038 : Taux élevé de conflits de verrou
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la documentation la plus récente sur Visual Studio, consultez [DA0038 : taux élevé de conflits de verrouillage](https://docs.microsoft.com/visualstudio/profiling/da0038-high-rate-of-lock-contentions).  
  
|||  
|-|-|  
|ID de la règle|DA0038|  
|Catégorie|Utilisation du .NET Framework|  
|Méthode de profilage|Échantillonnage<br /><br /> Instrumentation<br /><br /> Mémoire .NET|  
|Message|Un taux élevé de conflits de verrou .NET se produit. Analysez la raison de ce conflit de verrou en exécutant un profil Concurrence.|  
|Type de règle|Informations|  
  
 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 25 échantillons pour déclencher cette règle.  
  
## <a name="cause"></a>Cause  
 Les données relatives aux performances système qui sont collectées avec les données de profilage indiquent qu’un taux très élevé de conflits de verrouillage a été relevé lors de l’exécution de l’application. Effectuez un nouveau profilage à l’aide de la méthode de profilage d’accès concurrentiel pour rechercher la cause des conflits.  
  
## <a name="rule-description"></a>Description de la règle  
 Les verrous sont utilisés pour protéger des sections critiques du code qui doivent être exécutées séquentiellement par un thread à la fois dans une application multithread. Le common language runtime (CLR) Microsoft .NET fournit un ensemble complet de primitives de synchronisation et de verrouillage. Par exemple, le langage C# prend en charge l’instruction lock (SyncLock en Visual Basic). Une application managée peut appeler les méthodes `Monitor.Enter` et `Monitor.Exit` de l’espace de noms System. Threading pour acquérir et libérer un verrou directement. .NET Framework prend en charge d’autres primitives de synchronisation et de verrouillage, y compris des classes qui prennent en charge Mutex, ReaderWriterLock et Semaphore. Pour plus d’informations, consultez [Présentation des primitives de synchronisation](https://msdn.microsoft.com/library/ms228964.aspx) dans le guide du développeur .NET Framework, sur le site MSDN. Les classes .NET Framework sont elles-mêmes superposées à des services de synchronisation de niveau inférieur intégrés au système d’exploitation Windows. Ceux-ci incluent des objets section critiques, ainsi que de nombreuses fonctions d’attente (wait) et fonctions signalant des événements. Pour plus d’informations, consultez la section [Synchronisation](https://msdn.microsoft.com/library/ms686353.aspx) dans la documentation « Développement Win32 et COM » sur MSDN Library.  
  
 Derrière les classes .NET Framework et les objets Windows natifs qui sont utilisés pour la synchronisation et le verrouillage se trouvent des emplacements de mémoire partagée qui doivent être modifiés à l’aide d’opérations à blocage. Les opérations à blocage utilisent des instructions spécifiques au matériel qui opèrent sur des emplacements de mémoire partagée pour modifier leur état à l’aide d’opérations atomiques. Les opérations atomiques sont cohérentes sur tous les processeurs de l’ordinateur. Les objets Lock et WaitHandle sont des objets .NET qui utilisent automatiquement des opérations à blocage lorsqu’ils sont définis ou réinitialisés. D’autres structures de données de mémoire partagée de votre application peuvent nécessiter que vous utilisiez des opérations à blocage afin d’être mises à jour de manière thread-safe. Pour plus d’informations, consultez [Opérations à blocage](https://msdn.microsoft.com/library/sbhbke0y.aspx) dans la section .NET Framework de MSDN Library.  
  
 La synchronisation et le verrouillage sont des mécanismes qui permettent de garantir que les applications multithreads s’exécutent correctement. Chaque thread d’une application multithread est une unité d’exécution indépendante qui est planifiée indépendamment par le système d’exploitation. Un conflit de verrouillage se produit chaque fois qu’un thread qui tente d’acquérir un verrou est retardé à cause d’un autre thread qui détient le verrou.  
  
 Les verrous sont souvent imbriqués. L’imbrication se produit lorsqu’un thread qui exécute une section critique exécute une fonction qui nécessite alors un autre verrou. Un certain niveau d’imbrication de verrous est inévitable. Votre section critique peut appeler une méthode .NET Framework qui utilise des verrous pour s’assurer qu’elle est thread-safe. L’imbrication des verrous peut également se produire lorsqu’un appel est émis à partir d’une section critique de votre application dans une méthode .NET Framework qui verrouille également à l’aide d’un autre handle de verrou. L’imbrication des verrous peut entraîner des problèmes de performances qui sont connus pour être difficiles à résoudre.  
  
 Cette règle se déclenche lorsque les mesures prises pendant une exécution de profilage indiquent une quantité excessive de conflits de verrou. Les conflits de verrou retardent l’exécution des threads qui attendent le verrou. Vous devez toujours rechercher la cause des conflits de verrou, même lorsque vous exécutez des tests unitaires et des tests de charge sur du matériel bas de gamme et même si le niveau de conflit est peu important.  
  
> [!NOTE]
> Lorsque le taux de conflits de verrou signalés dans les données de profilage est très élevé, le message d’avertissement [DA0039 : Taux très élevé de conflits de verrou](../profiling/da0039-very-high-rate-of-lock-contentions.md) est déclenché à la place de ce message informatif.  
  
## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement  
 Double-cliquez sur le message pour accéder à la vue [Marques](../profiling/marks-view.md) des données de profilage.  Recherchez la colonne **Verrous et threads CLR .NET\Taux de conflits/s**. Déterminez s’il existe des phases spécifiques de l’exécution du programme durant lesquelles les conflits de verrou sont plus nombreux.  
  
 Cette règle se déclenche uniquement lorsque vous n’utilisez pas la méthode de profilage d’accès concurrentiel. Le profilage d’accès concurrentiel est la meilleure méthode pour diagnostiquer les problèmes de performances liés aux conflits de verrou dans votre application. Collectez des données de profilage d’accès concurrentiel pour mieux comprendre le comportement de verrouillage de votre application. Vous pourrez notamment connaître les verrous qui présentent le plus de conflits, le temps de retard de l’exécution de thread causé par l’attente de verrous en conflit, ainsi que la section de code impliquée. Les profils d’accès concurrentiel collectent des données sur tous les conflits de verrouillage, y compris le comportement de verrouillage des fonctionnalités Windows natives, des classes de .NET Framework et de toute autre bibliothèque tierce à laquelle votre application fait référence. Pour plus d’informations sur le profilage d’accès concurrentiel à partir de l’IDE de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], consultez [Collecte de données de concurrence de threads et de processus](../profiling/collecting-thread-and-process-concurrency-data.md). Pour plus d’informations sur le profilage d’accès concurrentiel à partir de la ligne de commande, consultez la section **Utilisation de la méthode de concurrence pour collecter les données de conflit de ressources et d’activité du thread** de la rubrique [Utilisation de méthodes de profilage à partir de la ligne de commande](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).
