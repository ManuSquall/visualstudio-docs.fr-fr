---
description: Récupère le nombre de modificateurs appliqués au type d’origine.
title: IDiaSymbol::get_numberOfModifiers | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 61ff7431-1994-4f7e-a182-1817f16f60a9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad43e11f45c005aad923cbb27e23865978d047d7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155935"
---
# <a name="idiasymbolget_numberofmodifiers"></a>IDiaSymbol::get_numberOfModifiers
Récupère le nombre de modificateurs appliqués au type d’origine.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_numberOfModifiers(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Pointeur vers un `DWORD` qui spécifie le nombre de modificateurs appliqués au type d’origine.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
