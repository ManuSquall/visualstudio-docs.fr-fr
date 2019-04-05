---
title: Raccordements d’allocation et Allocations de mémoire du runtime C | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9faacefd4fc0817f5dd5cae31392017458ede49e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952248"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Raccordements d'allocation et allocations de la mémoire runtime C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une restriction très importante s'applique aux fonctions de raccordement d'allocation : elles doivent ignorer de façon explicite les blocs `_CRT_BLOCK` (les allocations de mémoire effectuées en interne par les fonctions de la bibliothèque Runtime C) si elles passent des appels aux fonctions de la bibliothèque Runtime C qui allouent la mémoire interne. Vous pouvez ignorer les blocs `_CRT_BLOCK` en incluant un code, tel que le suivant au début de votre fonction de raccordement d'allocation :  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Si votre raccordement d'allocation n'ignore pas les blocs `_CRT_BLOCK`, toute fonction de la bibliothèque Runtime C appelée dans votre raccordement peut interrompre le programme dans une boucle sans fin. Par exemple, `printf` effectue une allocation interne. Si votre code de raccordement appelle `printf`, puis l’allocation résultante déclenchera votre raccordement d’être de nouveau appelée, laquelle va appeler **printf** à nouveau, et ainsi de suite jusqu'à ce que les dépassements de capacité de la pile. Si vous avez besoin de reporter les opérations d'allocation de `_CRT_BLOCK`, un moyen de contourner cette restriction consiste à utiliser pour la mise en forme et la sortie les fonctions API Windows, plutôt que les fonctions Runtime C. Étant donné que les API Windows n'utilisent pas le tas de la bibliothèque Runtime C, elles n'interrompront pas votre raccordement d'allocation dans une boucle sans fin.  
  
 Si vous examinez les fichiers sources de la bibliothèque Runtime, vous verrez que la fonction de raccordement d’allocation par défaut, à savoir **CrtDefaultAllocHook** (qui renvoie simplement **TRUE**), se trouve dans un fichier distinct, à savoir DBGHOOK.C. Si vous voulez que votre raccordement d’allocation soit appelé même pour les allocations effectuées par le code de démarrage runtime exécuté avant la fonction **main** de votre application, vous pouvez remplacer cette fonction par défaut par une fonction à vous, plutôt que d’utiliser [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d).  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, exemple](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
