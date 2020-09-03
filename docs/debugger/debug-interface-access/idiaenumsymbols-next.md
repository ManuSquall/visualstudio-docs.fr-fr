---
title: IDiaEnumSymbols::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Next method
ms.assetid: bfe5fe27-6a84-4392-910f-e325146d7552
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 110cacc241a733289b8cdce60c2d64c6fdf298e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467728"
---
# <a name="idiaenumsymbolsnext"></a>IDiaEnumSymbols::Next
Récupère un nombre spécifié de symboles dans la séquence d’énumération.

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

à Tableau à remplir avec les objets [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représentent les symboles souhaités.

 pceltFetched

à Retourne le nombre de symboles dans l’énumérateur extrait.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’y a plus de symboles. Sinon, retourne un code d'erreur.

## <a name="example"></a>Exemple

```C++
IDiaEnumSymbols* pEnum
CComPtr< IDiaSymbol> pSym;
DWORD celt;
pEnum->Next( 1, &pSym, &celt );
```

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)