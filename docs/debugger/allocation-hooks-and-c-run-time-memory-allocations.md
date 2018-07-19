---
title: Raccordements d’allocation et Allocations de mémoire du runtime C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e4c631b72ae9b12f77daf2ddd49919651c0b3e5
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433104"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Raccordements d'allocation et allocations de la mémoire runtime C
Une restriction très importante sur les fonctions de raccordement d’allocation est qu’elles doivent ignorer explicitement `_CRT_BLOCK` blocs. Ces blocs sont les allocations de mémoire effectuées en interne par les fonctions de bibliothèque Runtime C si elles passent des appels aux fonctions de bibliothèque Runtime C qui allouent la mémoire interne. Vous pouvez ignorer `_CRT_BLOCK` fonction de raccordement de blocs en incluant le code suivant au début de la répartition :  
  
```cpp
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Si votre raccordement d’allocation n’ignore pas `_CRT_BLOCK` bloque, puis une fonction de bibliothèque Runtime C appelée dans votre raccordement peut interrompre le programme dans une boucle sans fin. Par exemple, `printf` effectue une allocation interne. Si votre code de raccordement appelle `printf`, puis l’allocation résultante déclenchera votre raccordement d’être de nouveau appelée, laquelle va appeler **printf** à nouveau, et ainsi de suite, jusqu'à ce que les dépassements de capacité de la pile. Si vous avez besoin de reporter les opérations d'allocation de `_CRT_BLOCK`, un moyen de contourner cette restriction consiste à utiliser pour la mise en forme et la sortie les fonctions API Windows, plutôt que les fonctions Runtime C. Étant donné que les API Windows n’utilisez pas le tas de la bibliothèque Runtime C, ils n’intercepte pas votre raccordement d’allocation dans une boucle sans fin.  
  
 Si vous examinez les fichiers sources de bibliothèque du run-time, vous verrez que l’allocation par défaut fonction de raccordement, **CrtDefaultAllocHook** (qui renvoie simplement **TRUE**), se trouve dans un fichier distinct de son propre, DBGHOOK. C. Si vous souhaitez que votre raccordement d’allocation soit appelé même pour les allocations effectuées par le code de démarrage runtime exécuté avant de votre application **principal** (fonction), vous pouvez remplacer cette fonction par défaut par un des vôtres, au lieu de à l’aide de [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
