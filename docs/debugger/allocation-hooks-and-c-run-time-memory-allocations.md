---
title: Raccordements d'allocation et allocations de la mémoire runtime C
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be75b4d3e83ed297f31e9015c7ba082c0611206d
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851617"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Raccordements d'allocation et allocations de la mémoire runtime C
Une restriction très importante sur les fonctions de raccordement d’allocation est qu’elles doivent ignorer les blocs de manière explicite `_CRT_BLOCK` . Ces blocs sont les allocations de mémoire effectuées en interne par les fonctions de la bibliothèque Runtime C s’ils effectuent des appels à des fonctions de la bibliothèque Runtime C qui allouent de la mémoire interne. Vous pouvez ignorer `_CRT_BLOCK` les blocs en incluant le code suivant au début de votre fonction de raccordement d’allocation :

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

Si votre raccordement d’allocation n’ignore pas les `_CRT_BLOCK` blocs, toute fonction de la bibliothèque Runtime C appelée dans votre raccordement peut intercepter le programme dans une boucle sans fin. Par exemple, `printf` effectue une allocation interne. Si votre code de raccordement appelle `printf`, l’allocation résultante déclenchera un nouvel appel à votre raccordement, lequel rappellera **printf**, et ainsi de suite jusqu’à ce qu’un dépassement de capacité de la pile se produise. Si vous avez besoin de reporter les opérations d'allocation de `_CRT_BLOCK`, un moyen de contourner cette restriction consiste à utiliser pour la mise en forme et la sortie les fonctions API Windows, plutôt que les fonctions Runtime C. Étant donné que les API Windows n’utilisent pas le tas de la bibliothèque Runtime C, elles n’interceptent pas votre raccordement d’allocation dans une boucle sans fin.

Si vous examinez les fichiers sources de la bibliothèque Runtime, vous verrez que la fonction de raccordement d’allocation par défaut, à savoir **CrtDefaultAllocHook** (qui renvoie simplement **TRUE**), se trouve dans un fichier distinct, à savoir DBGHOOK.C. Si vous voulez que votre raccordement d’allocation soit appelé même pour les allocations effectuées par le code de démarrage runtime exécuté avant la fonction **main** de votre application, vous pouvez remplacer cette fonction par défaut par une fonction à vous, plutôt que d’utiliser [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).

## <a name="see-also"></a>Voir aussi
- [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)
