---
title: "Fonctions de raccordement d’allocation | Documents Microsoft"
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4fe5ac5ec207bb52884c097d1562a85a3414ba7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="allocation-hook-functions"></a>Fonctions de raccordement d'allocation
Une fonction de raccordement d’allocation, installée à l’aide de [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), est appelée chaque fois en mémoire est allouée, réallouée ou libérée. Ce type de raccordement a de multiples applications. Utilisez-la, par exemple, pour tester la façon dont une application gère les situations de mémoire insuffisante, pour examiner les modèles d’allocation ou pour enregistrer les informations des allocations en vue d’une analyse ultérieure.  
  
> [!NOTE]
>  Tenez compte des restrictions sur l’utilisation des fonctions de bibliothèque Runtime C dans une fonction de raccordement d’allocation, décrite dans [raccordements d’Allocation et Allocations de mémoire d’exécution C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Une fonction de raccordement d'allocation doit avoir un prototype similaire au suivant :  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Le pointeur que vous passez à [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) est de type **_CRT_ALLOC_HOOK**, comme défini dans CRTDBG. H :  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Lorsque la bibliothèque Runtime appelle votre raccordement, le *nAllocType* argument indique quelles allocation opération doit être effectuée (**_HOOK_ALLOC**, **_HOOK_REALLOC**, ou **_HOOK_FREE**). Dans le cas d'une libération ou d'une réallocation, `pvData` contient un pointeur vers la rubrique utilisateur du bloc qui va être libéré. Toutefois, dans le cas d'une allocation, ce pointeur est null, car l'allocation n'a pas encore eu lieu. Les autres arguments contiennent la taille de l’allocation concernée, son type de bloc, le numéro de requête séquentiel qui lui est associé et, le cas échéant, un pointeur vers le nom du fichier et le numéro de la ligne où l’allocation a été effectuée. Une fois que la fonction de raccordement effectue l’analyse et d’autres tâches voulues de son auteur, elle doit retourner **TRUE**, indiquant que l’opération d’allocation peut se poursuivre, ou **FALSE**, qui indique que le l’opération doit échouer. Un simple raccordement de ce type peut vérifier la quantité de mémoire allouée jusqu'à ce stade et retourner **FALSE** si cette quantité dépassait une petite limite. L'application serait alors confrontée au type d'erreurs d'allocation qui, en temps normal, survient uniquement lorsque la mémoire disponible est très faible. Des raccordements plus complexes permettraient d’assurer le suivi des modèles d’allocation, d’analyser l’utilisation de la mémoire ou de reporter des situations spécifiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Raccordements d’allocation et Allocations de mémoire du runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
