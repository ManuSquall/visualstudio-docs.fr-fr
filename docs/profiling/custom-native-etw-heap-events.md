---
title: Événements de tas ETW natifs personnalisés | Microsoft Docs
ms.date: 02/24/2017
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- C++
ms.workload:
- cplusplus
ms.openlocfilehash: 1414c2102d2b19728c8dfb74470fefae499bc622
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877135"
---
# <a name="custom-native-etw-heap-events"></a>Événements de tas ETW natifs personnalisés

Visual Studio contient de nombreux [outils de profilage et de diagnostic](../profiling/profiling-feature-tour.md), y compris un profileur de mémoire native.  Ce profileur raccorde les [événements ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) à partir du fournisseur de tas et fournit une analyse indiquant comment la mémoire est allouée et utilisée.  Par défaut, cet outil peut uniquement analyser les allocations effectuées à partir du tas Windows standard, et aucune allocation en dehors de ce tas natif n’est affichée.

Il existe de nombreux cas dans lesquels vous souhaiterez utiliser votre propre tas personnalisé et éviter la surcharge d’allocation liée au tas standard.  Par exemple, vous pouvez utiliser [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) pour allouer une grande quantité de mémoire au démarrage de l’application ou du jeu, puis gérer vos propres blocs dans cette liste.  Dans ce scénario, le profileur de mémoire voit uniquement cette allocation initiale, et pas la gestion personnalisée effectuée à l’intérieur du bloc de mémoire.  Toutefois, à l’aide du fournisseur ETW de tas natif personnalisé, vous pouvez laisser l’outil connaître toutes les allocations que vous effectuez en dehors du tas standard.

Par exemple, dans un projet comme le suivant où `MemoryPool` est un tas personnalisé, vous voyez une seule allocation sur le tas Windows :

```cpp
class Foo
{
public:
    int x, y;
};

...

// MemoryPool is a custom managed heap, which allocates 8192 bytes 
// on the standard Windows Heap named "Windows NT"
MemoryPool<Foo, 8192> mPool;

// the "allocate" method requests memory from the pool created above
// and is cast to an object of type Foo, shown above
Foo* pFoo1 = (Foo*)mPool.allocate();
Foo* pFoo2 = (Foo*)mPool.allocate();
Foo* pFoo3 = (Foo*)mPool.allocate();
```

Un instantané effectué à partir de l’outil [Utilisation de la mémoire](../profiling/memory-usage.md) sans suivi des tas personnalisés montrerait uniquement l’allocation de 8 192 octets, sans mention des allocations personnalisées effectuées par le pool :

![Allocation des tas Windows](media/heap-example-windows-heap.png)

En procédant aux étapes suivantes, nous pouvons utiliser ce même outil pour effectuer le suivi de l’utilisation de la mémoire dans notre tas personnalisé.

## <a name="how-to-use"></a>Utilisation

Cette bibliothèque peut facilement être utilisée en C et C++.

1. Incluez l’en-tête pour le fournisseur ETW de tas personnalisé :

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Ajoutez l’élément décoratif `__declspec(allocator)` à toute fonction dans votre gestionnaire de tas personnalisé qui retourne un pointeur vers la mémoire de tas nouvellement allouée.  Cet élément décoratif permet à l’outil d’identifier le type de la mémoire retournée.  Par exemple :

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```
   
   > [!NOTE]
   > Cet élément décoratif indique au compilateur que cette fonction est un appel à un allocateur.  Chaque appel à la fonction génère l’adresse du site d’appel, la taille de l’instruction d’appel et l’ID de type du nouvel objet dans un nouveau symbole `S_HEAPALLOCSITE`.  Quand une pile d’appels est allouée, Windows émet un événement ETW avec ces informations.  Le profileur de mémoire recherche, dans la pile d’appels, une adresse de retour correspondant à un symbole `S_HEAPALLOCSITE`, et les informations d’ID de type dans le symbole servent à afficher le type de runtime de l’allocation.
   >
   > En résumé, cela signifie qu’un appel qui ressemble à `(B*)(A*)MyMalloc(sizeof(B))` s’affiche dans l’outil comme étant de type `B`, et non `void` ou `A`.

1. Si vous utilisez C++, créez l’objet `VSHeapTracker::CHeapTracker`, en fournissant un nom pour le tas, qui s’affichera dans l’outil de profilage :

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   Dans le cas de C, utilisez la fonction `OpenHeapTracker` à la place.  Cette fonction retourne un handle qui permet d’appeler d’autres fonctions de suivi :
  
   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. Quand vous allouez de la mémoire à l’aide de votre fonction personnalisée, appelez la méthode `AllocateEvent` (C++) ou `VSHeapTrackerAllocateEvent` (C), en passant le pointeur désignant la mémoire et sa taille, pour effectuer le suivi de l’allocation :

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   ou

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > N’oubliez pas de baliser votre fonction d’allocateur personnalisée avec l’élément décoratif `__declspec(allocator)` décrit plus haut.

1. Quand vous désallouez de la mémoire à l’aide de votre fonction personnalisée, appelez la fonction `DeallocateEvent` (C++) ou `VSHeapTracerDeallocateEvent` (C), en passant le pointeur désignant la mémoire, pour effectuer le suivi de la désallocation :

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   ou :

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Quand vous réallouez de la mémoire à l’aide de votre fonction personnalisée, appelez la méthode `ReallocateEvent` (C++) ou `VSHeapReallocateEvent` (C), en passant un pointeur désignant la nouvelle mémoire, la taille de l’allocation et un pointeur désignant l’ancienne mémoire :

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   ou :

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. Enfin, pour fermer et nettoyer le dispositif de suivi du tas personnalisé en C++, utilisez le destructeur `CHeapTracker`, manuellement ou par le biais de règles de portée standard, ou la fonction `CloseHeapTracker` dans C :

   ```cpp
   delete pHeapTracker;
   ```

   ou :

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="track-memory-usage"></a>Suivre l’utilisation de la mémoire
Une fois ces appels en place, vous pouvez effectuer le suivi de l’utilisation du tas personnalisé à l’aide de l’outil **Utilisation de la mémoire** standard disponible dans Visual Studio.  Pour plus d’informations sur l’utilisation de cet outil, consultez la documentation [Memory Usage](../profiling/memory-usage.md) (Utilisation de la mémoire). Vous devez activer le profilage du tas avec des instantanés pour que l’utilisation du tas personnalisé s’affiche. 

![Activer le profilage du tas](media/heap-enable-heap.png)

Pour afficher le suivi de votre tas personnalisé, dans le coin supérieur droit de la fenêtre **Instantané**, ouvrez le menu déroulant **Tas**, puis, à la place de *Tas NT*, choisissez votre propre tas, tel que vous l’avez nommé.

![Sélection du tas](media/heap-example-custom-heap.png)

À l’aide de l’exemple de code ci-dessus, avec `MemoryPool` créant un objet `VSHeapTracker::CHeapTracker` et notre propre méthode `allocate` appelant la méthode `AllocateEvent`, vous pouvez maintenant voir le résultat de cette allocation personnalisée, qui affiche trois instances pour un total de 24 octets, toutes de type `Foo`.

Le tas *Tas NT* par défaut a le même aspect qu’auparavant, à ceci près que notre objet `CHeapTracker` lui a été ajouté.

![Tas NT avec dispositif de suivi](media/heap-example-windows-heap.png)

Comme avec le tas Windows standard, vous pouvez également utiliser cet outil pour comparer des instantanés et rechercher des fuites et des défaillances dans votre tas personnalisé, comme le décrit la documentation principale [Memory Usage](../profiling/memory-usage.md) (Utilisation de la mémoire).

> [!TIP]
> Visual Studio contient également un outil **Utilisation de la mémoire** dans l’ensemble d’outils de **profilage des performances**, que vous pouvez activer à l’aide de l’option de menu **Déboguer** > **Profileur de performances** ou de la combinaison de touches **Alt**+**F2**.  Cette fonctionnalité n’inclut pas le suivi de tas et n’affiche pas votre tas personnalisé comme décrit ici.  Cette fonctionnalité est uniquement disponible dans la fenêtre **Outils de diagnostic**, que vous pouvez activer avec le menu **Déboguer** > **Fenêtres** > **Afficher les outils de diagnostic** ou la combinaison de touches **Ctrl**+**Alt**+**F2**.

## <a name="see-also"></a>Voir aussi
[Découvrir les outils de profilage](../profiling/profiling-feature-tour.md)  
[Utilisation de la mémoire](../profiling/memory-usage.md)
