---
title: IDiaSymbol::get_liveRangeStartRelativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
ms.assetid: 1da52539-9872-4c20-8eaa-74b6cb5f3b02
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b73839b4d9ee0482fc8248b5ebd9f5c61f63552a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639048"
---
# <a name="idiasymbolgetliverangestartrelativevirtualaddress"></a>IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
Retourne le début de la plage d’adresses dans lequel le symbole local est valid.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_liveRangeStartRelativeVirtualAddress ( 
   DWORD* address
);
```

#### <a name="parameters"></a>Paramètres
 `address`

[out] Retourne le début de la plage d’adresses.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. L’adresse virtuelle relative retourné est le début de la plage dans laquelle le symbole est valide.

> [!NOTE]
>  Un code d’erreur renvoyé signifie que le symbole n’a pas d’informations sur la plage dynamique.

## <a name="remarks"></a>Remarques

## <a name="requirements"></a>Spécifications
 En-tête : Dia2.h

 Bibliothèque : diaguids.lib

 DLL : msdia100.dll

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)