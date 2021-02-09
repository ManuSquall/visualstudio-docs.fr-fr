---
title: Fonctions de raccordement d’allocation | Microsoft Docs
description: En savoir plus sur l’utilisation des fonctions de raccordement d’allocation, qui sont installées à l’aide de _CrtSetAllocHook, lorsque vous devez effectuer un débogage au moment de l’exécution C (CRT) dans Visual Studio.
ms.custom: SEO-VS-2020
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c032ca57e5a046a9f2dd2295226263ffe20f99e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858005"
---
# <a name="allocation-hook-functions"></a>Fonctions de raccordement d'allocation
Une fonction de raccordement d’allocation, installée à l’aide de [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), est appelée chaque fois que la mémoire est allouée, réallouée ou libérée. Vous pouvez utiliser ce type de raccordement à de nombreuses fins différentes. Utilisez-le pour tester la façon dont une application gère les situations de mémoire insuffisante, par exemple pour examiner les modèles d’allocation ou pour enregistrer les informations d’allocation pour une analyse ultérieure.

> [!NOTE]
> Tenez compte de la restriction concernant l’utilisation des fonctions de la bibliothèque Runtime C dans une fonction de raccordement d’allocation, décrite dans [Raccordements d’allocation et allocations de la mémoire runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).

 Une fonction de raccordement d’allocation doit avoir un prototype comme dans l’exemple suivant :

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 Le pointeur passé à [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) est du type **_CRT_ALLOC_HOOK**, comme cela est défini dans CRTDBG.H :

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 Lorsque la bibliothèque Runtime appelle votre raccordement, l’argument *nAllocType* indique l’opération d’allocation sur le point d’être effectuée (**_HOOK_ALLOC**, **_HOOK_REALLOC** ou **_HOOK_FREE**). Dans un gratuit ou dans une réallocation, `pvData` a un pointeur vers l’article utilisateur du bloc sur le point d’être libéré. Toutefois, pour une allocation, ce pointeur est null, car l’allocation n’a pas eu lieu. Les arguments restants contiennent la taille de l’allocation en question, son type de bloc, le numéro de requête séquentiel qui lui est associé et un pointeur vers le nom de fichier. S’ils sont disponibles, les arguments incluent également le numéro de ligne dans lequel l’allocation a été effectuée. Une fois que la fonction de raccordement a effectué l’analyse et les autres tâches voulues par son auteur, elle doit retourner **TRUE** pour indiquer que l’opération d’allocation peut se poursuivre, ou **FALSE** pour indiquer que l’opération doit échouer. Un simple raccordement de ce type pourrait vérifier la quantité de mémoire allouée jusqu’à ce stade et retourner **FALSE** si cette quantité dépassait une petite limite. L'application serait alors confrontée au type d'erreurs d'allocation qui, en temps normal, survient uniquement lorsque la mémoire disponible est très faible. Des raccordements plus complexes permettraient d'assurer le suivi des modèles d'allocation, d'analyser l'utilisation de la mémoire ou de reporter des situations spécifiques.

## <a name="see-also"></a>Voir aussi

- [Raccordements d’allocation et allocations de mémoire C Run-Time](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Écriture de la fonction de raccordement de débogage](../debugger/debug-hook-function-writing.md)