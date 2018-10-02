---
title: Raccordements d’allocation et Allocations de mémoire du runtime C | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3dbb9f2640d3da71566b8c8839b413943927af2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505036"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Raccordements d'allocation et allocations de la mémoire runtime C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [raccordements d’Allocation et Allocations de mémoire runtime C](https://docs.microsoft.com/visualstudio/debugger/allocation-hooks-and-c-run-time-memory-allocations).  
  
Une restriction très importante s'applique aux fonctions de raccordement d'allocation : elles doivent ignorer de façon explicite les blocs `_CRT_BLOCK` (les allocations de mémoire effectuées en interne par les fonctions de la bibliothèque Runtime C) si elles passent des appels aux fonctions de la bibliothèque Runtime C qui allouent la mémoire interne. Vous pouvez ignorer les blocs `_CRT_BLOCK` en incluant un code, tel que le suivant au début de votre fonction de raccordement d'allocation :  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Si votre raccordement d'allocation n'ignore pas les blocs `_CRT_BLOCK`, toute fonction de la bibliothèque Runtime C appelée dans votre raccordement peut interrompre le programme dans une boucle sans fin. Par exemple, `printf` effectue une allocation interne. Si votre code de raccordement appelle `printf`, puis l’allocation résultante déclenchera votre raccordement d’être de nouveau appelée, laquelle va appeler **printf** à nouveau, et ainsi de suite jusqu'à ce que les dépassements de capacité de la pile. Si vous avez besoin de reporter les opérations d'allocation de `_CRT_BLOCK`, un moyen de contourner cette restriction consiste à utiliser pour la mise en forme et la sortie les fonctions API Windows, plutôt que les fonctions Runtime C. Étant donné que les API Windows n'utilisent pas le tas de la bibliothèque Runtime C, elles n'interrompront pas votre raccordement d'allocation dans une boucle sans fin.  
  
 Si vous examinez les fichiers sources de bibliothèque du run-time, vous verrez que l’allocation par défaut fonction de raccordement, **CrtDefaultAllocHook** (qui renvoie simplement **TRUE**), se trouve dans un fichier distinct de son propre, DBGHOOK. C. Si vous souhaitez que votre raccordement d’allocation soit appelé même pour les allocations effectuées par le code de démarrage runtime exécuté avant de votre application **principal** (fonction), vous pouvez remplacer cette fonction par défaut par un des vôtres, au lieu de à l’aide de [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d).  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, exemple](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



