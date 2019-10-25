---
title: IDiaSymbol::get_types | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d23ea3c4d885b3f7575c998999814d0808d03bc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739055"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
Récupère un tableau de types spécifiques au compilateur pour ce symbole.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_types ( 
   DWORD       cTypes,
   DWORD*      pcTypes,
   IDiaSymbol* types[]
);
```

#### <a name="parameters"></a>Paramètres
 `cTypes`

dans Taille de la mémoire tampon pour stocker les données.

 `pcTypes`

à Retourne le nombre de types écrits ou, si le paramètre `types` est `NULL`, le nombre total de types disponibles.

 `types[]`

à Tableau à remplir avec les objets [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représentent tous les types pour ce symbole.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; Sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)