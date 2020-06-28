---
title: IDiaPropertyStorage::ReadULONGLONG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b188ec5067efed410d934b98559505d48ab6585a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466489"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
Lit les `ULONGLONG` valeurs dans un jeu de propriétés.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT ReadULONGLONG ( 
   PROPID     id,
   ULONGLONG* pValue
);
```

#### <a name="parameters"></a>Paramètres
 `id`

dans Identificateur de la propriété à lire ( `PROPID` défini dans WTypes. h en tant que `ULONG` ).

 `pValue`

à Retourne la valeur de la propriété.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne un code d’erreur. Retourne `E_INVALIDARG` si la propriété n’est pas de type `ULONGLONG` .

## <a name="remarks"></a>Remarques
 Un `ULONGLONG` est défini par Windows comme un entier non signé 64 bits.

## <a name="see-also"></a>Voir aussi
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)