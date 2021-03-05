---
description: Récupère un indicateur qui spécifie si la fonction a une convention d’appel personnalisée.
title: IDiaSymbol::get_customCallingConvention | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_customCallingConvention method
ms.assetid: 0aa97951-f7e1-4fa5-a87f-2920460c122d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 07254544c4f86bae494e16f5fa1914b7dee345c0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161022"
---
# <a name="idiasymbolget_customcallingconvention"></a>IDiaSymbol::get_customCallingConvention
Récupère un indicateur qui spécifie si la fonction a une convention d’appel personnalisée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_customCallingConvention(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

à Retourne `TRUE` si la fonction a une convention d’appel personnalisée ; sinon, retourne `FALSE` , la fonction a une convention d’appel connue.

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
