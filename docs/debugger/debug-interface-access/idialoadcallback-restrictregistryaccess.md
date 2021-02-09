---
title: IDiaLoadCallback::RestrictRegistryAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictRegistryAccess method
ms.assetid: de4760c3-a746-4bab-8065-1388fed31b67
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7cd793819bb0d8fdfb9e6c3b7c921c1dbf78ad22
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864678"
---
# <a name="idialoadcallbackrestrictregistryaccess"></a>IDiaLoadCallback::RestrictRegistryAccess
Détermine si les requêtes de Registre peuvent être utilisées pour rechercher des chemins de recherche de symboles.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT RestrictRegistryAccess();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Tout code de retour autre que `S_OK` empêche d’interroger le registre pour rechercher des chemins de recherche de symboles.

## <a name="see-also"></a>Voir aussi
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)