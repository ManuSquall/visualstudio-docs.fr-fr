---
title: IDiaSymbol::get_sealed | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_sealed method
ms.assetid: cd1fef1f-47de-47c7-885f-f6f0a9a07d8c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ece720a42b606640d02729951c11ae03d092aedf
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739359"
---
# <a name="idiasymbolget_sealed"></a>IDiaSymbol::get_sealed
Récupère un indicateur qui spécifie si la classe ou la méthode est sealed.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_sealed( 
   BOOL* pRetVal)
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si la classe ou la méthode est sealed ; Sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
 Une classe sealed ne peut pas être utilisée comme une classe de base. Une méthode sealed ne peut pas être substitué.

## <a name="requirements"></a>spécifications
 En-tête : Dia2. h

 Bibliothèque : diaguids. lib

 DLL : msdia100. dll

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)