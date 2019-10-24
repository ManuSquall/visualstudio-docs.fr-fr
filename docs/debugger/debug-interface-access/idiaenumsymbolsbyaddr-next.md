---
title: IDiaEnumSymbolsByAddr::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 424924f3fab62cf862420d58c947bba16343141d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743885"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
Récupère les symboles suivants dans l’ordre par adresse.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Next ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Paramètres
 celt

dans Nombre de symboles dans l’énumérateur à récupérer.

 rgelt

à Tableau à remplir avec l’objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente les symboles souhaités.

 pceltFetched

à Retourne le nombre de symboles dans l’énumérateur extrait.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’y a plus de symboles. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode met à jour la position de l’énumérateur en fonction du nombre d’éléments extraits.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)