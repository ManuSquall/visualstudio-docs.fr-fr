---
title: IDiaSymbol::findChildrenExByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByVA
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9cc9f540b200ff6fdf4736b6a0bf64175a5ee3e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741242"
---
# <a name="idiasymbolfindchildrenexbyva"></a>IDiaSymbol::findChildrenExByVA
Récupère les enfants du symbole qui sont valides à une adresse virtuelle spécifiée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findChildrenExByVA ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   DWORD             address,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `symtag`

dans Spécifie les balises de symboles des enfants à récupérer, comme défini dans l' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md). Affectez la valeur `SymTagNull` pour tous les enfants à récupérer.

 `name`

dans Spécifie le nom des enfants à récupérer. Affectez la valeur `NULL` pour tous les enfants à récupérer.

 `compareFlags`

dans Spécifie les options de comparaison à appliquer à la correspondance de noms. Les valeurs de l’énumération d' [énumération NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) peuvent être utilisées seules ou en combinaison.

 `address`

dans Spécifie l’adresse virtuelle.

 `ppResult`

à Retourne un objet [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) qui contient une liste des symboles enfants récupérés.

## <a name="return-value"></a>Valeur de retour
 Retourne `S_OK` si au moins un enfant du symbole a été trouvé, ou retourne `S_FALSE` si aucun enfant n’a été trouvé ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Les symboles locaux retournés incluent des informations de plage dynamique.

## <a name="requirements"></a>spécifications
 En-tête : Dia2. h

 Bibliothèque : diaguids. lib

 DLL : msdia100. dll

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md)