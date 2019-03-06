---
title: IDiaSymbol::get_localBasePointerRegisterId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_localBasePointerRegisterId method
ms.assetid: 9cbcaf00-9ace-45e1-b164-7a9439e08083
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f06a7109556836a63896fe2386c34f2451b97c1d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644690"
---
# <a name="idiasymbolgetlocalbasepointerregisterid"></a>IDiaSymbol::get_localBasePointerRegisterId
Récupère l’ID du Registre qui conserve un pointeur de base vers des variables locales sur la pile. Quand utiliser le [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) est défini sur `SymTagFunction`.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_localBasePointerRegisterId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne l’ID du Registre qui conserve un pointeur de base vers des variables locales sur la pile.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Remarques

## <a name="requirements"></a>Spécifications
 En-tête : Dia2.h

 Bibliothèque : diaguids.lib

 DLL : msdia100.dll

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)