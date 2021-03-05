---
description: Récupère un indicateur qui spécifie si des opérateurs de conversion sont définis pour le type de données défini par l’utilisateur.
title: IDiaSymbol::get_hasCastOperator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasCastOperator method
ms.assetid: a21114a6-56a3-4e8a-a65f-58ec2a0a8908
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f7b89c89bb2555edcfd70ac78dbe6a31a6af7fd8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160973"
---
# <a name="idiasymbolget_hascastoperator"></a>IDiaSymbol::get_hasCastOperator
Récupère un indicateur qui spécifie si des opérateurs de conversion sont définis pour le type de données défini par l’utilisateur.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_hasCastOperator ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne une valeur `TRUE` si le type de données défini par l’utilisateur a des opérateurs de cast définis ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
