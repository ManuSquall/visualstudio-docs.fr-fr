---
title: IDiaPropertyStorage::ReadLONG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af9d65c571c5e0a281b968d922c9b5170bd1c561
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742888"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
Lit `LONG` valeurs dans un jeu de propriétés.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT ReadDLONG ( 
   PROPID id,
   LONG*  pValue
);
```

#### <a name="parameters"></a>Paramètres
 `id`

dans Identificateur de la propriété à lire (`PROPID` est défini dans WTypes. h en tant que `ULONG`).

 `pValue`

à Retourne la valeur de la propriété.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur. Retourne `E_INVALIDARG` si la propriété n’est pas de type `LONG`.

## <a name="remarks"></a>Notes
 Une `LONG` est définie par Windows en tant qu’entier signé 32 bits.

## <a name="see-also"></a>Voir aussi
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)