---
title: IDiaSymbol::get_isSafeBuffers | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSafeBuffers method
ms.assetid: f29e373d-e7bb-4181-ab9f-bf708d401d83
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f4c3ab653c0a5540410d8e3e0b5426c4d0bcde5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740087"
---
# <a name="idiasymbolget_issafebuffers"></a>IDiaSymbol::get_isSafeBuffers
Récupère un indicateur qui spécifie si la directive de préprocesseur pour une mémoire tampon sécurisée est utilisée. Utilisez lorsque l' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) a la valeur `SymTagFunction`.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isSafeBuffers( 
   BOOL* pRetVal)
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si le pointeur utilise une directive de préprocesseur pour une mémoire tampon sécurisée ; Sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes

## <a name="requirements"></a>spécifications
 En-tête : Dia2. h

 Bibliothèque : diaguids. lib

 DLL : msdia100. dll

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [strict_gs_check](/cpp/preprocessor/strict-gs-check)