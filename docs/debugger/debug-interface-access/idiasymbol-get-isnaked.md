---
description: Récupère un indicateur qui spécifie si la fonction a l’attribut Naked () (autrement dit, si la fonction n’a pas de code de prologue ou d’épilogue ajouté par le compilateur).
title: IDiaSymbol::get_isNaked | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isNaked method
ms.assetid: b16629dc-8e17-476b-9c7b-58e7277c61ed
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ec1d273ce826a87ae658f7ed22fe7680edad25d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156159"
---
# <a name="idiasymbolget_isnaked"></a>IDiaSymbol::get_isNaked
Récupère un indicateur qui spécifie si la fonction a l’attribut [Naked](/cpp/cpp/naked-cpp) (autrement dit, si la fonction n’a pas de code de prologue ou d’épilogue ajouté par le compilateur).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isNaked(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

à Retourne `TRUE` si la fonction a l' `naked` attribut ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Appels de fonction Naked](/cpp/cpp/naked-function-calls)
