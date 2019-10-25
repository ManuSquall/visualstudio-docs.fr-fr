---
title: IDiaSymbol::get_typeIds | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4db7c1d7e3ed19268d94b28a7f0500788f7d21f5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739069"
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

à Retourne le nombre de `typeIds` écrits ou, si `typeIds` est `NULL`, le nombre total d’identificateurs de type disponibles.

 `typeIds[]`

à Tableau à remplir avec les identificateurs de type.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)