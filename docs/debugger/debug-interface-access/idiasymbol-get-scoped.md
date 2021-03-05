---
description: Récupère un indicateur qui spécifie si le type de données défini par l’utilisateur s’affiche dans une portée lexicale non globale.
title: IDiaSymbol::get_scoped | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_scoped method
ms.assetid: 588163f7-958e-4072-bf66-db5c5f07d3cb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 63260280f4730c2a0ee32324e49205650cd6c204
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161850"
---
# <a name="idiasymbolget_scoped"></a>IDiaSymbol::get_scoped
Récupère un indicateur qui spécifie si le type de données défini par l’utilisateur s’affiche dans une portée lexicale non globale.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_scoped ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si le type de données défini par l’utilisateur s’affiche dans une portée lexicale non globale ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
