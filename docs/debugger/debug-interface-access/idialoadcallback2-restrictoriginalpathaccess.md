---
description: Détermine s’il est possible de rechercher un fichier. pdb dans le répertoire de débogage d’origine.
title: IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7af6794b57dfe5efe8d2e85f8e74febcede5ef23
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157426"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Détermine s’il est possible de rechercher un fichier. pdb dans le répertoire de débogage d’origine.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Tout code de retour autre que `S_OK` empêche la recherche d’un fichier. pdb dans le répertoire de débogage d’origine. Le répertoire de débogage d’origine est le chemin d’accès au fichier de symboles compilé dans l’exécutable lorsque le débogage est activé. Ce chemin d’accès n’est pas nécessairement le même que le chemin d’accès de l’exécutable.

## <a name="see-also"></a>Voir aussi
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
