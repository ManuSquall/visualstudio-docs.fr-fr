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
ms.openlocfilehash: e52567eddcbb6c4f372256e66b7b723bc7aa7394
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56620172"
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

[in] Le nombre de symboles dans l’énumérateur à récupérer.

 rgelt

[out] Un tableau qui doit être rempli avec le [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet représentant les symboles de votre choisis.

 pceltFetched

[out] Retourne le nombre de symboles dans l’énumérateur extraite.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’existe plus aucun symbole. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Cette méthode met à jour la position de l’énumérateur par le nombre d’éléments extraits.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)