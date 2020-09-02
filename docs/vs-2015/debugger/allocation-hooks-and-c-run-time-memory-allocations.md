---
title: Raccordements d’allocation et allocations de mémoire Runtime C | Microsoft Docs
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
ms.openlocfilehash: 8487972c237b9c2ba6bf2594ffc1df43fa0c63cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702435"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Raccordements d'allocation et allocations de la mémoire runtime C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une restriction très importante s'applique aux fonctions de raccordement d'allocation : elles doivent ignorer de façon explicite les blocs `_CRT_BLOCK` (les allocations de mémoire effectuées en interne par les fonctions de la bibliothèque Runtime C) si elles passent des appels aux fonctions de la bibliothèque Runtime C qui allouent la mémoire interne. Vous pouvez ignorer les blocs `_CRT_BLOCK` en incluant un code, tel que le suivant au début de votre fonction de raccordement d'allocation :  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Si votre raccordement d'allocation n'ignore pas les blocs `_CRT_BLOCK`, toute fonction de la bibliothèque Runtime C appelée dans votre raccordement peut interrompre le programme dans une boucle sans fin. Par exemple, `printf` effectue une allocation interne. Si votre code de raccordement appelle `printf` , l’allocation résultante entraîne le rappel de votre raccordement, qui appelle **printf** à nouveau, et ainsi de suite jusqu’à ce que la pile déborde. Si vous avez besoin de reporter les opérations d'allocation de `_CRT_BLOCK`, un moyen de contourner cette restriction consiste à utiliser pour la mise en forme et la sortie les fonctions API Windows, plutôt que les fonctions Runtime C. Étant donné que les API Windows n'utilisent pas le tas de la bibliothèque Runtime C, elles n'interrompront pas votre raccordement d'allocation dans une boucle sans fin.  
  
 Si vous examinez les fichiers sources de la bibliothèque Runtime, vous verrez que la fonction de raccordement d’allocation par défaut, à savoir **CrtDefaultAllocHook** (qui renvoie simplement **TRUE**), se trouve dans un fichier distinct, à savoir DBGHOOK.C. Si vous voulez que votre raccordement d’allocation soit appelé même pour les allocations effectuées par le code de démarrage runtime exécuté avant la fonction **main** de votre application, vous pouvez remplacer cette fonction par défaut par une fonction à vous, plutôt que d’utiliser [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d).  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de la fonction de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [Exemple de crt_dbg2](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
