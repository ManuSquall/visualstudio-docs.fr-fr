---
title: IDiaSymbol::get_typeIds | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 31cff55617e21c8ed750800fec982f2b1492d977
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862569"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
Récupère un tableau des valeurs d’identificateur de type spécifiques au compilateur pour ce symbole.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>Paramètres
 `cTypeIds`

dans Taille de la mémoire tampon pour stocker les données.

 `pcTypeIds`

à Retourne le nombre de `typeIds` écrits ou, si `typeIds` a `NULL` la valeur, le nombre total d’identificateurs de type disponibles.

 `typeIds[]`

à Tableau à remplir avec les identificateurs de type.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)