---
title: IDiaSession::findSymbolsForAcceleratorPointerTag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 72510e9e82c1ec6983075880d4335dee8c0ad23c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839236"
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
Retourne une énumération des symboles pour la variable la valeur de balise spécifiée correspond à de la fonction de stub accélérateur page parente.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findSymbolsForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `parent`

[in] IDiaSymbol qui correspond à la fonction de stub accélérateur à rechercher.

 `tagValue`

[in] La valeur de balise de pointeur.

 `ppResult`

[out] Un pointeur vers un `IDiaEnumSymbols` pointeur d’interface qui est initialisé avec le résultat.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)