---
title: Les Versions Debug des fonctions d’Allocation de tas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12b997b2aeb2b34305eafc2dc478460d9f450677
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941464"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Versions Debug des fonctions d'allocation du tas
La bibliothèque Runtime C contient des versions Debug spéciales des fonctions d'allocation du tas. Ces fonctions utilisent les noms des versions Release, suivis de _dbg. Cette rubrique décrit les différences entre la version Release d’une fonction CRT et la version _dbg à partir d’exemples basés sur `malloc` et `_malloc_dbg`.  
  
 Lorsque [_DEBUG](/cpp/c-runtime-library/debug) est défini, le CRT mappe tous les [malloc](/cpp/c-runtime-library/reference/malloc) appelle à [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Il est donc inutile de réécrire votre code en utilisant `_malloc_dbg` à la place de `malloc` pour bénéficier de ses avantages pendant le débogage.  
  
 Vous pouvez cependant appeler `_malloc_dbg` de façon explicite. Un appel explicite à `_malloc_dbg` présente en outre les avantages suivants :  
  
- suivi des allocations de type `_CLIENT_BLOCK` ;  
  
- stockage du fichier source et du numéro de la ligne où la demande d'allocation a été effectuée.  
  
  Si vous ne souhaitez pas convertir votre `malloc` appelle à `_malloc_dbg`, vous pouvez obtenir les informations du fichier source en définissant [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), ce qui provoque le mappage de préprocesseur directement tous les appels à `malloc` à `_malloc_dbg` au lieu d’utiliser un wrapper autour de `malloc`.  
  
  Pour effectuer le suivi des différents types d'allocations dans les blocs client, vous devez appeler `_malloc_dbg` directement et affecter au paramètre `blockType` la valeur `_CLIENT_BLOCK`.  
  
  Lorsque _DEBUG n’est pas défini, les appels à `malloc` ne sont pas perturbés, les appels à `_malloc_dbg` sont résolus en `malloc`, la définition de [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) est ignorée et la source de fichier les informations se rapportant à la demande d’allocation n’est pas fournie. Dans la mesure où `malloc` ne possède aucun paramètre de type de bloc, les demandes de types `_CLIENT_BLOCK` sont traitées comme des allocations standard.  
  
## <a name="see-also"></a>Voir aussi  
 [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md)