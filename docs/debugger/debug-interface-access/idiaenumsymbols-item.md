---
title: IDiaEnumSymbols::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Item method
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12766fe52f7f515b7ca411b17d58117e4e56cc9f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743948"
---
# <a name="idiaenumsymbolsitem"></a>IDiaEnumSymbols::Item
Récupère un symbole au moyen d’un index.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD        index,
   IDiaSymbol** symbol
);
```

#### <a name="parameters"></a>Paramètres
 index

dans Index de l’objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) à récupérer. L’index se trouve dans la plage 0 à `count`-1, où `count` est retourné par la méthode [IDiaEnumSymbols :: get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) .

 symbole

à Retourne un objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) représentant le symbole souhaité.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)