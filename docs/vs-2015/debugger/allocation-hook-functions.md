---
title: Fonctions de raccordement d’allocation | Microsoft Docs
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8d2aff47737443b998cfae8d16c3d95a5eb1d2a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952962"
---
# <a name="allocation-hook-functions"></a>Fonctions de raccordement d'allocation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une fonction de raccordement d’allocation, installée à l’aide de [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d), est appelée chaque fois la mémoire est allouée, réallouée ou libérée. Ce type de raccordement a de multiples applications. Utilisez-la, par exemple, pour tester la façon dont une application gère les situations de mémoire insuffisante, pour examiner les modèles d'allocation ou pour enregistrer les informations des allocations en vue d'une analyse ultérieure.  
  
> [!NOTE]
>  Tenez compte de la restriction concernant l’utilisation des fonctions de la bibliothèque Runtime C dans une fonction de raccordement d’allocation, décrite dans [Raccordements d’allocation et allocations de la mémoire runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Une fonction de raccordement d'allocation doit avoir un prototype similaire au suivant :  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Le pointeur passé à [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d) est du type **_CRT_ALLOC_HOOK**, comme cela est défini dans CRTDBG.H :  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Lorsque la bibliothèque Runtime appelle votre raccordement, le *nAllocType* argument indique quelles allocation opération est sur le point d’être effectuée (**_HOOK_ALLOC**, **_HOOK_REALLOC**, ou **_HOOK_FREE**). Dans le cas d'une libération ou d'une réallocation, `pvData` contient un pointeur vers la rubrique utilisateur du bloc qui va être libéré. Toutefois, dans le cas d'une allocation, ce pointeur est null, car l'allocation n'a pas encore eu lieu. Les autres arguments contiennent la taille de l’allocation concernée, son type de bloc, le numéro de requête séquentiel qui lui est associé et, le cas échéant, un pointeur vers le nom du fichier et le numéro de la ligne où l’allocation a été effectuée. Une fois que la fonction de raccordement a effectué l’analyse et les autres tâches voulues par son auteur, elle doit retourner **TRUE** pour indiquer que l’opération d’allocation peut se poursuivre, ou **FALSE** pour indiquer que l’opération doit échouer. Un simple raccordement de ce type pourrait vérifier la quantité de mémoire allouée jusqu’à ce stade et retourner **FALSE** si cette quantité dépassait une petite limite. L'application serait alors confrontée au type d'erreurs d'allocation qui, en temps normal, survient uniquement lorsque la mémoire disponible est très faible. Des raccordements plus complexes permettraient d'assurer le suivi des modèles d'allocation, d'analyser l'utilisation de la mémoire ou de reporter des situations spécifiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Raccordements d’allocation et allocations mémoire Runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, exemple](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
