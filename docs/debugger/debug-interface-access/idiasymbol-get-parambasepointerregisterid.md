---
title: IDiaSymbol::get_paramBasePointerRegisterId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_paramBasePointerRegisterId method
ms.assetid: 9f5caeb4-5c88-4054-bf8b-50d34bbbf8c5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09bdfb5d276e4dc7414c78529c2a6f1644597cd3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739514"
---
# <a name="idiasymbolget_parambasepointerregisterid"></a>IDiaSymbol::get_paramBasePointerRegisterId
Récupère l’ID du Registre qui contient un pointeur de base vers les paramètres. Utilisez lorsque l' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) a la valeur `SymTagFunction`.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_paramBasePointerRegisterId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne l’ID du Registre qui contient un pointeur de base vers les paramètres.

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