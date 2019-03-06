---
title: IDiaSymbol::get_targetRelativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetRelativeVirtualAddress method
ms.assetid: 49a159f3-6943-44d3-90a3-0dba51e8a7ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13c0d42dbfdbe5016e4072bc3473da31f20b0752
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611696"
---
# <a name="idiasymbolgettargetrelativevirtualaddress"></a>IDiaSymbol::get_targetRelativeVirtualAddress
Récupère l’adresse virtuelle relative (RVA) d’une cible de conversion de code.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_targetRelativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne l’adresse RVA d’une cible de conversion de code.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Remarques
 Cette propriété est valide uniquement si le symbole comme un [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) valeur `SymTagThunk`.

 Une conversion de « code » est un morceau de code qui effectue la conversion entre un espace d’adressage de mémoire de 32 bits (également appelé espace d’adresse plat) et un espace d’adressage de 16 bits (appelé un espace d’adressage segmentés).

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)