---
title: IDiaSymbol::findChildrenExByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByRVA
ms.assetid: cbc57c6c-7d64-4469-a114-1dd6671e5ec5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 936aa9006fac088efbb155d44ca8e4257ce94302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464568"
---
# <a name="idiasymbolfindchildrenexbyrva"></a>IDiaSymbol::findChildrenExByRVA
Récupère les enfants du symbole qui sont valides à une adresse virtuelle relative (RVA) spécifiée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findChildrenExByRVA ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   DWORD             address,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `symtag`

dans Spécifie les balises de symboles des enfants à récupérer, comme défini dans l' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md). Affectez à la valeur `SymTagNull` pour tous les enfants à récupérer.

 `name`

dans Spécifie le nom des enfants à récupérer. Affectez à la valeur `NULL` pour tous les enfants à récupérer.

 `compareFlags`

dans Spécifie les options de comparaison à appliquer à la correspondance de noms. Les valeurs de l’énumération d' [énumération NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) peuvent être utilisées seules ou en combinaison.

 `address`

dans Spécifie l’adresse RVA.

 `ppResult`

à Retourne un objet [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) qui contient une liste des symboles enfants récupérés.

## <a name="return-value"></a>Valeur renvoyée
 Retourne `S_OK` si au moins un enfant du symbole a été trouvé, ou retourne `S_FALSE` si aucun enfant n’a été trouvé ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Les symboles locaux retournés incluent des informations de plage dynamique.

## <a name="requirements"></a>Configuration requise
 En-tête : Dia2. h

 Bibliothèque : diaguids. lib

 DLL : msdia100.dll

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md)