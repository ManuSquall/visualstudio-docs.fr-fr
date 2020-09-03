---
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d94e38ade7b44d7458a0918080214d00e0000aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466608"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
Lit les `BOOL` valeurs dans un jeu de propriétés.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT ReadBOOL ( 
   PROPID id,
   BOOL*  pValue
);
```

#### <a name="parameters"></a>Paramètres
 `id`

dans Identificateur de la propriété à lire ( `PROPID` défini dans WTypes. h en tant que `ULONG` ).

 `pValue`

à Retourne la valeur de la propriété.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne un code d’erreur. Retourne `E_INVALIDARG` si la propriété n’est pas de type `BOOL` .

## <a name="remarks"></a>Notes
 Pour obtenir des résultats cohérents, interpréter la `BOOL` valeur de sorte que les valeurs autres que zéro soient `TRUE` et zéro est `FALSE` .

## <a name="see-also"></a>Voir aussi
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)