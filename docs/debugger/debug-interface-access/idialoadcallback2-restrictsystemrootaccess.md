---
title: IDiaLoadCallback2::RestrictSystemRootAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictSystemRootAccess method
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2e9c3a144ccde9f6464db6f5b84f36aa5eac5668
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864655"
---
# <a name="idialoadcallback2restrictsystemrootaccess"></a>IDiaLoadCallback2::RestrictSystemRootAccess
Détermine si la recherche de fichiers. pdb est autorisée dans le répertoire racine système.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT RestrictSystemRootAccess();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Tout code de retour autre que `S_OK` empêche la recherche de fichiers. pdb dans la racine système.

## <a name="see-also"></a>Voir aussi
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)