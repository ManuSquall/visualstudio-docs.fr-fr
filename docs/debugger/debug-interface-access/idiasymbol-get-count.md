---
title: IDiaSymbol::get_count | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_count method
ms.assetid: f6d6ac2f-6d96-4f88-962b-29c0a66890b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3b50210c3f214870c287fe2cd5228a3ab5af464
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611566"
---
# <a name="idiasymbolgetcount"></a>IDiaSymbol::get_count
Récupère le nombre d’éléments dans une liste ou un tableau.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_count ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne le nombre d’éléments dans une liste ou un tableau.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>Spécifications

|Spécification|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)