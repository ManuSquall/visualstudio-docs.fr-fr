---
title: Fonctions de raccordement d’allocation | Microsoft Docs
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c8a051641811da3658ffe556982c67649704069
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433354"
---
# <a name="allocation-hook-functions"></a>Fonctions de raccordement d'allocation
Une fonction de raccordement d’allocation, installée à l’aide de [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), est appelée chaque fois la mémoire est allouée, réaffectée ou libérée. Vous pouvez utiliser ce type de raccordement pour de nombreux scénarios différents. Utilisez-le pour tester comment une application gère les situations de mémoire insuffisante, par exemple pour examiner les modèles d’allocation, ou enregistrer des informations d’allocation pour une analyse ultérieure.  
  
> [!NOTE]
>  N’oubliez pas de la restriction sur l’utilisation des fonctions de bibliothèque Runtime C dans une fonction de raccordement d’allocation, décrite dans [raccordements d’Allocation et Allocations de mémoire runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Une fonction de raccordement d’allocation doit avoir un prototype comme dans l’exemple suivant :  
  
```cpp
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Le pointeur que vous passez à [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) est de type **_CRT_ALLOC_HOOK**, tel que défini dans CRTDBG. H :  
  
```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Lorsque la bibliothèque Runtime appelle votre raccordement, le *nAllocType* argument indique quelles allocation opération est sur le point d’être apportées (**_HOOK_ALLOC**, **_HOOK_REALLOC**, ou **_HOOK_FREE**). Dans un gratuit ou dans une réallocation, `pvData` possède un pointeur vers l’article de l’utilisateur du bloc qui va être libéré. Toutefois d’allocation, ce pointeur est null, car l’allocation n’a pas encore s’est produite. Les autres arguments contiennent la taille de l’allocation concernée, son type de bloc, le numéro de requête séquentiel associée et un pointeur vers le nom de fichier. S’il est disponible, les arguments incluent également le numéro de ligne dans laquelle l’allocation a été effectuée. Une fois que la fonction de raccordement effectue l’analyse et les autres tâches veut de son auteur, elle doit retourner **TRUE**, indiquant que l’opération d’allocation peut se poursuivre, ou **FALSE**, qui indique que le opération doit échouer. Un simple raccordement de ce type peut vérifier la quantité de mémoire allouée jusqu'à ce stade et retourner **FALSE** si cette quantité dépassait une petite limite. L'application serait alors confrontée au type d'erreurs d'allocation qui, en temps normal, survient uniquement lorsque la mémoire disponible est très faible. Des raccordements plus complexes permettraient d’assurer le suivi des modèles d’allocation, d’analyser l’utilisation de la mémoire ou de reporter des situations spécifiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Raccordements d’allocation et Allocations de mémoire du runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
