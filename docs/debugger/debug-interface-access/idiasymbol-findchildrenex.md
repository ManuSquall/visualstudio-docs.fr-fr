---
title: IDiaSymbol::findChildrenEx | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenEx
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26fdced012baada390cdd0a112856b592d3c923e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741271"
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
Récupère les enfants du symbole. Les symboles locaux retournés incluent des informations de plage dynamique, si le programme est compilé avec l’optimisation sur.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findChildrenEx ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
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

 `ppResult`

à Retourne un objet [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) qui contient une liste des symboles enfants récupérés.

## <a name="return-value"></a>Valeur de retour
 Retourne `S_OK` si au moins un enfant du symbole a été trouvé, ou retourne `S_FALSE` si aucun enfant n’a été trouvé ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est la version étendue de [IDiaSymbol :: findchildren (](../../debugger/debug-interface-access/idiasymbol-findchildren.md).

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