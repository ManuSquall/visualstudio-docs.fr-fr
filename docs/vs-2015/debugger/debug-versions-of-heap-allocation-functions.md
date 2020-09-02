---
title: Versions Debug des fonctions d’allocation du tas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 13f8d8b79ecf586048aacf3cd9442c596f184be3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691159"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Versions Debug des fonctions d'allocation du tas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La bibliothèque Runtime C contient des versions Debug spéciales des fonctions d'allocation du tas. Ces fonctions utilisent les noms des versions Release, suivis de _dbg. Cette rubrique décrit les différences entre la version Release d’une fonction CRT et la version _dbg à partir d’exemples basés sur `malloc` et `_malloc_dbg`.  
  
 Lorsque [_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) est défini, le CRT mappe tous les appels [malloc](https://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) à [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb). Il est donc inutile de réécrire votre code en utilisant `_malloc_dbg` à la place de `malloc` pour bénéficier de ses avantages pendant le débogage.  
  
 Vous pouvez cependant appeler `_malloc_dbg` de façon explicite. Un appel explicite à `_malloc_dbg` présente en outre les avantages suivants :  
  
- suivi des allocations de type `_CLIENT_BLOCK` ;  
  
- stockage du fichier source et du numéro de la ligne où la demande d'allocation a été effectuée.  
  
  Si vous ne souhaitez pas convertir vos `malloc` appels à `_malloc_dbg` , vous pouvez obtenir les informations du fichier source en définissant [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b), ce qui amène le préprocesseur à mapper directement tous les appels à `malloc` à au `_malloc_dbg` lieu de s’appuyer sur un wrapper `malloc` .  
  
  Pour effectuer le suivi des différents types d'allocations dans les blocs client, vous devez appeler `_malloc_dbg` directement et affecter au paramètre `blockType` la valeur `_CLIENT_BLOCK`.  
  
  Lorsque _DEBUG n’est pas défini, les appels à ne `malloc` sont pas perturbés, les appels à `_malloc_dbg` sont résolus en `malloc` , la définition de [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b) est ignorée et les informations du fichier source appartenant à la demande d’allocation ne sont pas fournies. Dans la mesure où `malloc` ne possède aucun paramètre de type de bloc, les demandes de types `_CLIENT_BLOCK` sont traitées comme des allocations standard.  
  
## <a name="see-also"></a>Voir aussi  
 [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md)
