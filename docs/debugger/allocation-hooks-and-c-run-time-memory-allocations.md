---
title: "Raccordements d’allocation et Allocations de mémoire d’exécution C | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.hooks
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
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62a8be3b1a1c98a330efeb26d9a84e74f2334423
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Raccordements d'allocation et allocations de la mémoire runtime C
Une restriction très importante s'applique aux fonctions de raccordement d'allocation : elles doivent ignorer de façon explicite les blocs `_CRT_BLOCK` (les allocations de mémoire effectuées en interne par les fonctions de la bibliothèque Runtime C) si elles passent des appels aux fonctions de la bibliothèque Runtime C qui allouent la mémoire interne. Vous pouvez ignorer les blocs `_CRT_BLOCK` en incluant un code, tel que le suivant au début de votre fonction de raccordement d'allocation :  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Si votre raccordement d'allocation n'ignore pas les blocs `_CRT_BLOCK`, toute fonction de la bibliothèque Runtime C appelée dans votre raccordement peut interrompre le programme dans une boucle sans fin. Par exemple, `printf` effectue une allocation interne. Si votre code de raccordement appelle `printf`, l’allocation résultante ne lèvera pas votre raccordement d’être de nouveau appelée, laquelle va appeler **printf** à nouveau, et ainsi de suite jusqu'à ce que les dépassements de capacité de la pile. Si vous avez besoin de reporter les opérations d'allocation de `_CRT_BLOCK`, un moyen de contourner cette restriction consiste à utiliser pour la mise en forme et la sortie les fonctions API Windows, plutôt que les fonctions Runtime C. Étant donné que les API Windows n'utilisent pas le tas de la bibliothèque Runtime C, elles n'interrompront pas votre raccordement d'allocation dans une boucle sans fin.  
  
 Si vous examinez les fichiers sources de bibliothèque Runtime, vous verrez que l’allocation par défaut fonction de raccordement, **CrtDefaultAllocHook** (qui renvoie simplement **TRUE**), se trouve dans un fichier distinct qui lui sont propres, DBGHOOK. C. Si vous souhaitez que votre raccordement d’allocation soit appelé même pour les allocations effectuées par le code de démarrage runtime qui est exécuté avant de votre application **principal** (fonction), vous pouvez remplacer cette fonction par défaut par celle de votre choix, à la place de à l’aide de [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, exemple](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)