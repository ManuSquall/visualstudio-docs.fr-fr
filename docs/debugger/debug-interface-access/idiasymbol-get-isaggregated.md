---
description: Récupère un indicateur qui spécifie si le symbole de données fait partie d’un agrégat ou d’une collection de symboles ; le compilateur traite les symboles agrégés comme des entités distinctes, mais ils font véritablement partie d’un symbole unique plus grand.
title: IDiaSymbol::get_isAggregated | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isAggregated method
ms.assetid: 24d280ef-6ea3-4958-9418-4ad3ca7c67c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e78ec7f180ad1c719d562975377a413156bb1480
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160861"
---
# <a name="idiasymbolget_isaggregated"></a>IDiaSymbol::get_isAggregated
Récupère un indicateur qui spécifie si le symbole de données fait partie d’un agrégat ou d’une collection de symboles ; le compilateur traite les symboles agrégés comme des entités distinctes, mais ils font véritablement partie d’un symbole unique plus grand.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isAggregated(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

à Retourne `TRUE` si les données font partie d’une agrégation de symboles fractionnés à partir d’un symbole parent ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
 La méthode [IDiaSymbol :: get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md) est `TRUE` pour le symbole qui est le parent des symboles agrégés.

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)
