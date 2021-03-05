---
description: Récupère un indicateur qui spécifie si le module est un. netmodule (un module MSIL (Microsoft Intermediate Language) qui contient uniquement des métadonnées et aucun symbole natif).
title: IDiaSymbol::get_isMSILNetmodule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isMSILNetmodule method
ms.assetid: 593827f3-8437-4a12-ada4-ff715ec95fb2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 27d1294e5cbced8cd2f521a25858a37efe9f5b8c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160763"
---
# <a name="idiasymbolget_ismsilnetmodule"></a>IDiaSymbol::get_isMSILNetmodule
Récupère un indicateur qui spécifie si le module est un. netmodule (un module MSIL (Microsoft Intermediate Language) qui contient uniquement des métadonnées et aucun symbole natif).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isMSILNetmodule(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

à Retourne `TRUE` si le module est MSIL ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
 Cette propriété est disponible à partir du `SymTagCompilandDetails` type de symbole (consultez [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)).

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)
