---
title: IDiaPropertyStorage::ReadBSTR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6e87c2ed168a262fc1a12f06fc6a18bcf73e7bc
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466594"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Lit les `BSTR` valeurs dans un jeu de propriétés.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>Paramètres
 `id`

dans Identificateur de la propriété à lire ( `PROPID` défini dans WTypes. h en tant que `ULONG` ).

 `pValue`

à Retourne la valeur de la propriété.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne un code d’erreur. Retourne `E_INVALIDARG` si la propriété n’est pas de type `BSTR` .

## <a name="remarks"></a>Remarques
 Un `BSTR` est défini par Windows comme une chaîne de caractères larges se terminant par zéro.

## <a name="see-also"></a>Voir aussi
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)