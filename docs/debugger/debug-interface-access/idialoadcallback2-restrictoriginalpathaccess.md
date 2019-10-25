---
title: IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bcdaa7c1896a0ef29706e3650ad8ac56537f778
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743000"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Détermine s’il est possible de rechercher un fichier. pdb dans le répertoire de débogage d’origine.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Tout code de retour autre que `S_OK` empêche la recherche d’un fichier. pdb dans le répertoire de débogage d’origine. Le répertoire de débogage d’origine est le chemin d’accès au fichier de symboles compilé dans l’exécutable lorsque le débogage est activé. Ce chemin d’accès n’est pas nécessairement le même que le chemin d’accès de l’exécutable.

## <a name="see-also"></a>Voir aussi
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)