---
title: IDiaSymbol::get_function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_function method
ms.assetid: 48b3a318-3211-410f-8570-c02ee210f0a5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4702b121161bd73639d580faa13f502e89d8be3d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64806696"
---
# <a name="idiasymbolgetfunction"></a>IDiaSymbol::get_function
Récupère un indicateur qui spécifie si les symboles publics fait référence à une fonction.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_function ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne un `TRUE` si le symbole fait référence à une fonction ; sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d’erreur.

> [!NOTE]
> La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>Configuration requise

|Prérequis|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)